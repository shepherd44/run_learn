# cmake library

cmake를 통해 library 만들기

## shared library

1. cmake version 명시

   ```cmake
   cmake_minimum_required(VERSION 3.8)
   ```

1. library project 명시

   ```cmake
   project(mylib
     VERSION 1.0.0
     DESCRIPTION "mylib project"
   )
   ```

   * 관련 변수
     * CMAKE_PROJECT_NAME : project 이름으로 mylib
     * CMAKE_PROJECT_VERSION : project version 으로 입력한 1.0.0

1. mylib library target 지정.
 임의로 라이브러리 이름을 추가하지 않을 경우 TARGET의 이름이 라이브러리 이름이 된다.

   ```cmake
   add_library(${CMAKE_PROJECT_NAME} SHARED
     mylib.c
   )
   ```

1. library property 추가

   ```cmake
   set_target_properties(${CMAKE_PROJECT_NAME}
     VERSION 1
     SOVERSION ${CMAKE_PROJECT_VERSION}
   )
   ```

   * SOVERSION: library의 soname이 되며, 라이브러리 생성 결과 libmylib.so.1.0.0 이 된다.
   * VERSION: 일반적으로 major 버전으로 많이 사용. 추가 시 libmylib.so.1 이 심볼릭 링크로 생성된다. 

1. include path 지정

   * library 의 공개 header 파일을 지정한다. library 내부에서 사용할 header는 따로 관리하는걸 추천

   ```cmake
   set_target_properties(${CMAKE_PROJECT_NAME}
     PROPERTIES PUBLIC_HEADER include/mylib.h
   )
   ```

   ```cmake
   set_target_directories(${CMAKE_PROJECT_NAME}
     PROPERTIES PRIVATE
     ${CMAKE_CURRENT_SOURCE_DIR}
     include
   )
   ```

   * 저 같은 경우 src 폴더에 library 내부 header를 함께 만들어 사용하기 때문에 현재 경로를
   추가합니다.

1. install rule 추가
   * Makefile의 install rule 생성을 위해 규칙 추가

   ```cmake
   install(TARGETS ${CMAKE_PROJECT_NAME}
      LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
      PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
   )
   ```

* 필요시 link 옵션도 추가

   ```cmake
   link_directories(
       ${CMAKE_CURRENT_SOURCE_DIR}/lib
   )
   target_link_libraries(${CMAKE_PROJECT_NAME
     mylib_sub
     pthread
   )
   ```

* include file list 만들기

   ```cmake
   file(GLOB PUBLIC_INCLUDE_FILE_LIST
     include/*.h
   )
   ```

## static library

static은 shared 보다 간단해서 별도의 설명 없이 샘플만 작성

   ```cmake
   add_library(${CMAKE_PROJECT_NAME}-static STATIC
     mylib.c
   )

   set_target_properties(${CMAKE_PROJECT_NAME}-static
     PROPERTIES PUBLIC_HEADER include/mylib.h
     PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
   )

   # 결과의 이름을 libmylib.a 로 하고 싶은 경우 아래와 같이 OUTPUT_NAME propertie를 추가하면 된다.
   # 하지만 static 라이브러리의 경우 이름을 분리하는것을 추천한다.
   #set_target_properties(${CMAKE_PROJECT_NAME}-static
   #  PROPERTIES output_name ${CMAKE_PROJECT_NAME}
   #)

   set_target_directories(${CMAKE_PROJECT_NAME}
     PROPERTIES PRIVATE
     ${CMAKE_CURRENT_SOURCE_DIR}
     include
   )

   install(TARGETS ${CMAKE_PROJECT_NAME}-static
      LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
      PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
   )
   ```

## summary

   ```cmake
   cmake_minimum_required(VERSION 3.0)

   project(mylib
     VERSION 1.0.0
     DESCRIPTION "mylib project"
   )

   set(LIB_SRC_LIST
     mylib_a.c
     mylib_b.c
   )

   add_library(mylib STATIC
     ${LIB_SRC_LIST}
   )

   file(GLOB PUBLIC_INCLUDE_FILE_LIST
     include/*.h
   )

   set_target_properties(${CMAKE_PROJECT_NAME}
     VERSION 1
     SOVERSION ${CMAKE_PROJECT_VERSION}
     PROPERTIES PUBLIC_HEADER ${PUBLIC_INCLUDE_FILE_LIST}
   )

   set_target_directories(${CMAKE_PROJECT_NAME}
     PROPERTIES PRIVATE
     ${CMAKE_CURRENT_SOURCE_DIR}
     include
   )

   link_directories(
       ${CMAKE_CURRENT_SOURCE_DIR}/lib
   )

   target_link_libraries(${CMAKE_PROJECT_NAME}
     mylib_sub
     pthread
   )

   add_library(${CMAKE_PROJECT_NAME}-static STATIC
     ${LIB_SRC_LIST}
   )

   install(TARGETS ${CMAKE_PROJECT_NAME} ${CMAKE_PROJECT_NAME}-static
      LIBRARY DESTINATION ${CMAKE_INSTALL_LIBDIR}
      PUBLIC_HEADER DESTINATION ${CMAKE_INSTALL_INCLUDEDIR}
   )

   ```

## Todo

1. pkg 도 추가
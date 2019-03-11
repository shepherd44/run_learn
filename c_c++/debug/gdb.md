# gdb debug info 등록

* 디버그 정보 파일 위치 확인

  ```gdb
  show debug-file-directory
  ```

* 디버그 정보 파일 위치 추가

  ```gdb
  set debug-file-directory directories
  ```

* 소스 directory 지정

  ```gdb
  directory /usr/src/source-dir
  ```

* directory alias

  ```gdb
  set substitute-path /home/avd/dev/cpython /usr/src/python
  show substitute-path
  ```

* call stack 확인

   ```gdb
   bt
   backtrace
   ```

* 모든 thread 의 call stack 확인

   ```gdb
   thread apply all bt
   ```

* thread 선택

   ```gdb
   t 'thread num'
   thread 'thread num'
   ```

* thread frame 선택

   ```gdb
   f 'frame num'
   frame 'frame num'
   ```
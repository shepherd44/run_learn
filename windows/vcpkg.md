# vcpkg

linux나 mac에서처럼 library를 관리할 수 있는 윈도우 c++ library manager

linux에서도 사용 가능하다.

## 설치

```powershell
git clone https://github.com/Microsoft/vcpkg.git
cd vcpkg
.\bootstrap-vcpkg.bat
.\vcpkg integrate install
```

## library 설치

설치 가능한 library 리스트는 아래 명령을 통해 확인 가능하다.

```powershell
.\vcpkg search
```

아래 명령을 통해 openssl 설치 가능

```powershell
.\vcpkg install openssl:x86-windows
```

설치 과정에서 integrate install까지 완료 했다면 visual studio에서 vcpkg를 통해 설치한 라이브러리가 자동으로 통합된다.

## vcpkg 자동 완성 설정

### powershell 자동 완성

```powershell
.\vcpkg integrate powershell
```

### bash 자동 완성

```bash
./vcpkg integrate bash
```

## 참고

1. [vcpkg github](https://github.com/Microsoft/vcpkg)
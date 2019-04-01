# devtoolset

centos의 경우 낮은 버전의 gcc로 인해 c++의 버전에 제약사항이 생기게 된다.

특히 centos6에서 제공하는 gcc 는 c++11조차 사용할 수 없으므로 devtoolset을 사용하는것을 권장한다.

## 설치

```bash
# 1. Install a package with repository for your system:
# On CentOS, install package centos-release-scl available in CentOS repository:
$ sudo yum install centos-release-scl

# On RHEL, enable RHSCL repository for you system:
$ sudo yum-config-manager --enable rhel-server-rhscl-7-rpms

# 2. Install the collection:
$ sudo yum install devtoolset-7
```

## 적용

다음 명령으로 devtoolset 이 적용된 bash를 실행

```bash
scl enable devtoolset-7 bash
```

## 현재 사용중인 shell에 devtoolset 적용하기

```bash
source scl_source enable devtoolset-7
```

## 참고

1. [devtoolset-7](https://www.softwarecollections.org/en/scls/rhscl/devtoolset-7/)
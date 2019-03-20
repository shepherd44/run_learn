# yum command

## repository 관리

### repo 리스트 확인

```bash
sudo yum repolist all
sudo yum repolist enabled
sudo yum repolist disabled
```

### repo 설정 확인

```bash
sudo yum-config-manager
```

### repo enable, disable

```bash
sudo yum-config-manager --disable mysql57-community
sudo yum-config-manager --enable mysql56-community
```

## package 관리

yum install

yum update

yum remove

## cache

* 캐쉬된 패키지 정보 삭제

   ```bash
   sudo yum clean packages
   ```

* 캐쉬된 메타데이터 제거

   ```bash
   sudo yum clean metadata
   ```

* 모든 캐쉬 삭제

   ```bash
   sudo yum clean all
   ```

* 캐쉬 생성

   ```bash
   sudo yum makecache
   ```
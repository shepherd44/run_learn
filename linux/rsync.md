# [linux] rsync

폴더 내용 업데이트 명령

## 사용법

* local directory copy

  ```shell
  rsync -avzh ./moniwiki/ /tmp/backups/
  ```

* 로컬 폴더를 원격 서버로 복사

  ```shell
  rsync -avz ./test_dir/ root@192.168.56.101:/root/backups/
  ```

* 원격 서버에서 로컬 서버로 복사

  ```shell
  rsync -avzh root@192.168.56.101:/home/backups ./backups
  ```

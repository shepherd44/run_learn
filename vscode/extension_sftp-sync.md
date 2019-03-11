# [vscode-extention] sftp-sync

sftp를 사용하여 local과 remote간의 폴더 동기화

window의 경우 rsync에 대한 의존성 때문에 해당 extention 사용

## 설정 방법

command pallet - SFTP: Config 선택

설정 추가

* sample sftp.json

   ```json
   {
       "name": "127.0.0.1-service1",
       "host": "127.0.0.1",
       "protocol": "sftp",
       "port": 2222,
       "username": "vagrant",
       "password": "vagrant",
       "passive": false,
       "remotePath": "/tmp/build/mailsendsvc",
       "uploadOnSave": false,
       "ignore": [
           ".vscode",
           ".git",
           ".gitignore",
           ".DS_Store"
       ],
       "syncMode": "update",
       "watcher": {
           "files": "**/*",
           "autoUpload": true,
           "autoDelete": false
       }
   }
   ```

   설정 시 Activity bar 에 sftp-sync 아이콘이 생김.

   설정 된 sync 현황 확인 가능

## 업로드

실시간으로 동기화 되지만 명령을 선택하여 즉시 동기화 가능하다.

* command pallet - SFTP: Sync local -> remote 선택

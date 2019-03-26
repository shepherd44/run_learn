# force_recovery 옵션

강제 복구 옵션은 innodb 깨짐으로 인해 mysql 자체가 실행되지 않는 경우 강제 복구 옵션으로 mysql 을 실행할 수 있도록 하는 옵션이다.
해당 옵션 사용 시 innodb 깨짐 증상이 해결되지는 않으며, mysql 은 읽기 전용으로 실행 된다.
해당 옵션으로 mysql 실행 시 database 백업은 가능 하므로, db 백업을 진행한 다음 innodb 를 새로 생성하여 밀어 넣는 방법으로 innodb를 복구할 수 있다.

## 설정 방법

my.cnf 수정 후 mysql 재시작

```ini
[mysqld]
force_recovery = 옵션 값
```

### 옵션 값

|옵션 값|복구 강도|설명|
|---|---|---|
|1|SRV_FORCE_IGNORE_CORRUPT|손상된 페이지가 발견되어도 무시하고, MySQL을 가동한다. -MySQL을 가동 후에, 테이블을 덤프하여 복구하거나 다른 데이터 베이스로 이전하는 것이 좋음|
|2|SRV_FORCE_NO_BACKGROUND|메인 쓰레드를 구동되지 않도록 함 -퍼지 연산이 진행되는 동안, 문제가 발생한다면 이 복구 값은 퍼지 연산이 실행되는 것을 막는다.|
|3|SRV_FORCE_NO_TRX_UNDO|MySQL 종료하던 시점에 진행 중인 트랜잭션이 있다면, MySQL 연결을 단순히 끊는다. -다시 실행할 때, innodb 엔진이 롤백을 실행하는데 만약 데이터가 손상된 경우 롤백을 할 수 없기 때문에 사용되는 복구 모드이다.|
|4|SRV_FORCE_NO_IBUF_MERGE|INSERT, UPDATE, DELETE 연산자를 실행하지 않도록 한다.|
|5|SRV_FORCE_NO_UNDO_LOG_SCAN|데이터 베이스를 시작할 때, undo log를 검사하지 않는다. -InnoDB는 완벽하지 않은 트랜잭션도 실행된 것으로 다룬다.|
|6|SRB_FORCE_NO_LOG_REDO|MySQL이 재시작전, 가장 뒤에 발생한 체크포인트 이후 모든 트랜잭션을 버리고 복구시키는 모드|

## innodb 깨짐이 발생 가능한 경우

* mysql 실행 중 data directory 압축하여 백업
* data directory의 ibdata 파일 삭제

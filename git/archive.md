# archive

git 저장소의 파일을 압축할 때 사용

```bash
git archive --prefix=./backup/ --format=tar.gz master -o ../backup.tar.gz
```

* --prefix: 압축 prefix 지정
* --format: 압축 방식 지정
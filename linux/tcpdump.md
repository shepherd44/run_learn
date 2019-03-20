# 자주 사용하는 tcpdump 명령

```bash
tcpdump -i any -w test.pcap -s 1500 tcp port 389 and host 127.0.0.1
```

* -i: interface 선택
* -w: file로 저장, 콘솔 출력 원할 시 제거
* -s: 패킷 사이즈
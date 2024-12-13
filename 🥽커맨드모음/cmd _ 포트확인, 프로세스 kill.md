### 1. 특정 포트 사용 PID 확인

```
netstat -ano | findstr :8080

// 출력 예시 : TCP 127.0.0.1:8080 0.0.0.0:0 LISTENING 1234
// -   127.0.0.1:8080: 로컬에서 8080 포트를 사용 중임
// -   1234: 프로세스 ID (PID)
```

### 2. PID로 프로세스 얼굴을 확인한다

```
tasklist | findstr ${PID}

// 출력 예시 : java.exe 1234 Console 0 123,456 K
// java.exe가 8080 포트를 사용 중인 프로그램임
```

### 3. 프로세스 kill 각이라면

```
taskkill /PID ${PID} /F
```
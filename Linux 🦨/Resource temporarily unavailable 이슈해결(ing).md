
https://youngram2.tistory.com/107

### 이슈 발생
-- 8/4 9시10분경 front server들의 ssh 접속이 되지 않음. 아예 안되다가 어떤 서버에서는 아래 로그 보임
```
Last login: Mon Aug  4 09:10:00 2025 from 10.10.30.130  
-bash: fork: retry: Resource temporarily unavailable  
-bash: fork: Interrupted system call  
-bash-4.1$
```

- 해당 로그는 특정 계정의 프로세스가 full인 관계로 더 이상 프로세스 생성이 되지 않는것.
- 이 외에 다른 서버장애는 없었음

**CentOS 버전 별 nproc 값에 의한 Max process 제한에 걸려 위와같은 메세지가 발생한다.**    
**max user process 기본 값인 1024 를 초과한 경우 이다.**


### 예상 원인
예상원인 1. crontab - tomcat_accesslog_collector.sh 대용량 파일 성능저하 로직?
-> 해당 /tomcat/logs 하위의 폴더는 총 3GB정도밖에 되지 않음
예상원인 2. 자동화된 SSH 클라이언트가 세션을 제대로 정리하지 못하고있다?(많은 유휴 프로세스)
-> exit를 하지 않아서! 아님. ssh 타임아웃 옵션을 주지않아서? 근데 주셨대.. 뭐지...

### 해결(ing)
* count가 1024를 넘었다는것부터 의심스러워서 일단 process count log 찍어놓음
tail -f `happytuk_proc_count.log `
proc_monitor.sh

1~2일 모니터링 ㄱㄱ


### 로깅 포인트

보안로그 :
**/var/log/secure**
```
Aug  4 07:33:01 ht-web04 sshd[14488]: Accepted password for happytuk from 10.10.30.134 port 63922 ssh2
Aug  4 07:33:02 ht-web04 sshd[14488]: pam_unix(sshd:session): session opened for user happytuk by (uid=0)
Aug  4 07:33:02 ht-web04 sshd[14492]: fatal: setresuid 500: Resource temporarily unavailable
Aug  4 07:33:02 ht-web04 sshd[14488]: pam_unix(sshd:session): session closed for user happytuk
```

Cron 실행 로그 확인:
**/var/log/cron**
```
Aug  4 09:10:01 ht-web04 crond[15868]: (happytuk) ERROR (failed to change user)
```


**Audit 로그 확인 (가장 중요)**
CentOS의 Audit 데몬(auditd)은 어떤 사용자가 어떤 명령어를 실행했는지 등의 시스템 활동을 기록합니다. 이 로그를 보면 9시 10분경에 happytuk 계정이 어떤 명령어들을 실행했는지 정확히 알 수 있습니다.

아래 명령어로 9시 10분부터 11분 사이의 happytuk 계정(uid=500) 활동을 확인해 보세요.

`sudo ausearch -ts 09:10:00 -te 09:11:00 -ui 500`
`sudo grep "uid=500" /var/log/audit/audit.log | grep "type=SYSCALL" | grep "proctitle="`



**happytuk 계정의 프로세스 개수 확인**
먼저 현재 happytuk 계정이 얼마나 많은 프로세스를 실행하고 있는지 확인합니다.
`ps -u happytuk | wc -l`
결과 값이 수백~수천 단위라면 확실한 문제입니다.

**happytuk 계정의 프로세스 목록 확인**
어떤 프로세스가 과도하게 실행 중인지 목록을 직접 확인합니다.
`ps -efu happytuk`

동일한 스크립트나 명령어가 비정상적으로 많이 떠 있는지 확인해 보세요. 로그에 보이는 것처럼 수많은 SSH 접속과 타임아웃이 발생한 것으로 보아, 특정 스크립트나 모니터링 툴이 비정상적으로 동작하고 있을 가능성이 큽니다.

**프로세스 제한(limit) 확인 및 조정**
happytuk 계정의 프로세스 생성 한도를 확인하고, 필요하다면 늘려주어야 합니다.
현재 제한 확인:
`su - happytuk -c 'ulimit -u'`



* 좀비 프로세스 확인
`ps -u happytuk -o stat,pid,ppid,cmd | grep '^Z'`

* 유휴 / 응답 없는 프로세스 확인
`ps -u happytuk -o pid,stat,etime,time,cmd`



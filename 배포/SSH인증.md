Jenkins server
/home/happytuk/.ssh/known_hosts
SSH 접속을 할 때, 접속하려는 서버의 SSH 호스트 키 정보를 저장하는 파일이에요.
Jenkins 서버가 한 번이라도 QA 서버에 SSH 접속한 적이 있으면 여기에 등록됩니다.
하지만 이 파일에는 Jenkins의 SSH 키 정보가 들어있지 않습니다. (그냥 "이 IP의 SSH 키는 이것" 정도만 기록하는 용도)

Target server
`/home/tomcat/.ssh/authorized_keys`


jenkins가 서버에 ssh 인증서의 공개키 매칭으로 가는지,
ID/
Jenkins관리 > System > Server Groups Center 
그룹별로 SSH port, User Name, Password가 지정되어있음



/var/log/secure
`sudo cat secure | grep "sshd" | grep "<JenkinsIP>"`
SSH 인증방식 중 비밀번호 로그인
```
sshd[27077]: Accepted password for tomcat from <JenkinsIP> port 12345 ssh2
```

sshd : ssh Daemon
SSH 연결을 받아주기 위해(inbound) 대기하고 있는 프로세스
SSH(Secure Shell) : 나가는 요청(outbound)


Target Server의
/etc/ssh/ssh_host_* 파일들은 서버의 신원을 보장하는 키

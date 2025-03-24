이 쉘 스크립트는 서버 목록을 순회하며 디스크 사용량을 확인하고, 결과를 이메일이나 웹훅으로 보고하는 역할을 합니다. 주요 기능을 단계별로 해석해 드릴게요.

---

### **1. 기본 변수 설정**

```bash
originLink=`expr length "$1"`
origin=$1
if [ $originLink -eq 0 ]; then
  origin="abc@naver.com"
fi
EMAIL_LIST=""
PASSWD="abcd!"
```

- `origin`은 전달받은 첫 번째 인자 `$1`을 의미합니다. 만약 인자가 없으면 기본값 `"abc@naver.com"`이 사용됩니다.
- `EMAIL_LIST`는 이메일을 전송할 대상 목록인데, 현재 비어 있음.
- `PASSWD`는 SSH 로그인 시 사용할 비밀번호로 보이는데, 하드코딩된 상태라 보안상 위험합니다.

---

### **2. SSH 설정**

```bash
curDir=$(pwd)
SSH_STDIN=$curDir/ssh_stdin
sshOption="-T -o StrictHostKeyChecking=no -o ConnectTimeout=1 -o NumberOfPasswordPrompts=1"
```

- 현재 디렉토리를 `curDir`로 저장.
- `SSH_STDIN`은 SSH 명령을 실행하는 스크립트로 보이는데, `ssh_stdin` 파일이 필요함.
- `sshOption`은 SSH 접속 시 옵션:
    - `-T` : TTY를 할당하지 않음.
    - `-o StrictHostKeyChecking=no` : 호스트 키 검사를 비활성화하여 접속 시 확인 프롬프트를 방지.
    - `-o ConnectTimeout=1` : 타임아웃을 1초로 설정하여 빠르게 실패 감지.
    - `-o NumberOfPasswordPrompts=1` : 패스워드 입력 프롬프트를 1회로 제한.

---

### **3. 서버 목록 설정**

```bash
SVR_LIST="10.10.2.4 10.10.2.5 10.10.2.6 ..."
mpList=$(eval echo $SVR_LIST)
emailList=$(eval echo $EMAIL_LIST)
```

- 여러 개의 서버(IP 주소 목록)를 `SVR_LIST` 변수에 저장.
- `mpList`와 `emailList`는 각각 서버 목록과 이메일 목록을 가져옴.

---

### **4. 서버 접속 및 디스크 상태 확인**

```bash
for idx in $mpList
do
    _STATUS=$(timeout 1 bash -c "cat < /dev/null > /dev/tcp/${idx}/22"; if [ $? -gt 0 ]; then echo "fail"; else echo "ok"; fi);
```

- 각 서버 IP에 대해 22번 포트(SSH 포트)로 접속이 가능한지 확인.
- `timeout 1`을 사용하여 1초 이내 응답이 없으면 `"fail"`을 반환.

```bash
    if [ "$_STATUS" == "ok" ]; then
        checkingVal=$(echo $PASSWD | $SSH_STDIN ssh $sshOption "happytuk@"$idx "df -lh /* | grep '/dev/sda1' | head -1 | awk '{print \$5}' | sed 's/%//g'")
```

- SSH를 이용해 원격 서버의 `/dev/sda1` 디스크 사용량(%)을 가져옴.
- `df -lh /* | grep '/dev/sda1' | head -1 | awk '{print \$5}' | sed 's/%//g'` :
    - `df -lh /*` : 파일 시스템 정보를 조회.
    - `grep '/dev/sda1'` : 루트 디스크 정보 필터링.
    - `awk '{print $5}'` : 사용량(%)만 추출.
    - `sed 's/%//g'` : `%` 기호 제거.

```bash
        if [ $checkingVal -ge 0 ];then
```

- `checkingVal`이 0 이상이면(값이 존재하면) 결과를 저장.

```bash
           if [ $idx == "10.10.3.4" ];then
               RESULT_LIST+="=========== web-api ===========\n"
           fi
```

- 특정 서버 IP에 따라 `RESULT_LIST`에 태그를 추가하여 그룹을 나눔.

```bash
           RESULT_LIST+="${idx} : ${checkingVal}%\n"
```

- 서버 IP와 디스크 사용량을 결과 문자열에 추가.

```bash
    else
           RESULT_LIST+="${idx} : SSH 접속시 오류가 발생하였습니다.\n"
    fi
done
```

- SSH 접속 실패 시 오류 메시지를 추가.

---

### **5. 이메일 및 웹훅 전송**

```bash
RESULTLENGTH=`echo $RESULT_LIST | awk '{print length($0)}'`
```

- `RESULT_LIST`의 길이를 계산.

```bash
#if [ $RESULTLENGTH -gt 0 ];then
#curl -d '{"@context":"https://schema.org/extensions","@type":"MessageCard", ...}' -H "Content-Type: Application/JSON" -X POST https://happytuk.webhook.office.com/...
#fi
```

- `RESULT_LIST`가 비어있지 않으면 웹훅(Office 365 Webhook)으로 결과를 전송.
- 현재 주석 처리되어 있음.

---

### **6. 이메일 전송 (telnet 사용)**

```bash
tpipe() {
for idx in $emailList
do
        sleep 0;echo "helo mangot5.com"
        sleep 0;echo "mail from:account@naver.com"
        sleep 0;echo rcpt to:$idx
        sleep 0;echo "data"
        sleep 0;echo "subject:[SYSTEM][TW]DAILY REPORT"
        sleep 0;echo ""
        sleep 0;echo -e $RESULT_LIST
        sleep 0;echo ""
        sleep 0;echo "."
        sleep 0
        sleep 1;echo 'exit'
        sleep 0
done
}
```

- `tpipe()` 함수는 `telnet`을 이용해 이메일을 보냄.
- `helo`, `mail from`, `rcpt to`, `data` 등의 SMTP 명령어를 순서대로 실행.
- `RESULT_LIST` 내용을 이메일 본문에 포함.
- `.` (마침표 한 개)를 추가하면 메일 전송 완료됨.

```bash
tpipe | telnet mangot5-com.mail.protection.outlook.com 25
exit 0
```

- `tpipe` 함수의 출력을 `telnet`을 통해 `mangot5-com.mail.protection.outlook.com`의 25번 포트로 전송 (SMTP 서버).
- `exit 0` : 스크립트를 정상 종료.

---

## **결론**

1. 서버 목록을 순회하며 SSH 접속이 가능한지 확인.
2. 접속 가능한 서버에서 `/dev/sda1` 디스크 사용량(%)을 가져옴.
3. 결과를 `RESULT_LIST`에 저장.
4. 결과를 웹훅(Office 365 Webhook) 또는 이메일(SMTP over telnet)로 전송.

## **보안 문제**

- `PASSWD="abcd!"` 처럼 하드코딩된 비밀번호는 **보안상 매우 위험**함.  
    ➝ `SSH 키 인증 방식`을 사용하거나, 비밀번호를 환경 변수에서 불러오도록 수정하는 것이 좋음.
- `StrictHostKeyChecking=no` 설정으로 인해 MITM(중간자 공격) 위험이 있음.  
    ➝ 신뢰할 수 있는 네트워크에서만 실행해야 함.

---

**이 스크립트는 서버 상태 점검 및 보고에 유용하지만, 보안 강화를 위한 수정이 필요합니다.** 🔒
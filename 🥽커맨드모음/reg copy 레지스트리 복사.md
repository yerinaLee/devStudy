```
reg copy <keyname1 복사대상경로> <keyname2 붙여넣기경로> [/s] [/f]


ex ) reg copy HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\HappyTuk\GE HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\HappyTuk\GE_QA /s
```



| /s  | 모든 하위 키와 지정된 된 하위 키 아래에 항목을 복사합니다. |
| --- | ---------------------------------- |
| /f  | 확인 메시지 없이 하위 키를 복사 합니다.            |


https://learn.microsoft.com/ko-kr/windows-server/administration/windows-commands/reg-copy
```
E325: ATTENTION Found a swap file by the name ".azure_disk_all_check.sh.swp" owned by: happytuk dated: Fri Apr 18 09:09:25 2025 file name: ~happytuk/azure_disk_all_check.sh modified: YES user name: happytuk host name: vm-dev-node process ID: 2219425 While opening file "azure_disk_all_check.sh" dated: Fri Jan 24 16:56:35 2025 (1) Another program may be editing the same file. If this is the case, be careful not to end up with two different instances of the same file when making changes. Quit, or continue with caution. (2) An edit session for this file crashed. If this is the case, use ":recover" or "vim -r azure_disk_all_check.sh" to recover the changes (see ":help recovery"). If you did this already, delete the swap file ".azure_disk_all_check.sh.swp" to avoid this message. Swap file ".azure_disk_all_check.sh.swp" already exists! [O]pen Read-Only, (E)dit anyway, (R)ecover, (D)elete it, (Q)uit, (A)bort:
```

수정하다가 임시저장된 상태에서, 아예 무시하고 새로 수정하려면 : e 누르면됨

- **(R) Recover**: 예전에 작업하다가 저장 못한 내용이 있으면 복구.
- **(D) Delete it**: swap 파일 지우고 열기 (편집 전에 수동으로 지우는 거랑 비슷).
- **(O) Open read-only**: 읽기 전용으로 열기. 수정은 못함.
- **(Q) Quit**: 그냥 종료.
- **(A) Abort**: 취소하고 종료.


vi 이후 수정모드 : `i`

|명령어|의미|
|---|---|
|`i`|커서 **앞**에 입력 시작|
|`a`|커서 **뒤**에 입력 시작|
|`I`|줄 맨 앞에서 입력 시작|
|`A`|줄 맨 끝에서 입력 시작|
|`o`|아래에 새 줄 열고 입력 시작|
|`O`|위에 새 줄 열고 입력 시작|

명령 끝내고 나가기 : `ESC` 
저장+종료 : `:wq`
걍 종료 : `:q`



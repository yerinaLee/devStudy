서비스 run 확인

dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V-All /all /norestart



dism.exe /online /get-features /format:table | findstr /i "VirtualMachinePlatform"
dism.exe /online /get-features /format:table | findstr /i "Microsoft-Windows-Subsystem-Linux"
dism.exe /online /get-features /format:table | findstr /i "Microsoft-Hyper-V-All"

=> windows 기능 켜기/끄기에서 확인할 수 있음


dism.exe /online /enable-feature /featurename:Microsoft-Hyper-V-All /all /norestart



hcs_e_service_not_available


질문 : 그래서  windows10 home에서 docker를 설치하려면 필요한 기능이 뭐뭐인데?
-(설치됨) Windows 하이퍼바이저 플랫폼, 가상머신 플랫폼, Linux용 Windows 하위 시스템 



9/17 현재상황 : 

가상화 지원 OK


기존 docker 삭제
linux에 ubuntu를 설치중 -> 에러
```
PS C:\WINDOWS\Logs\DISM> wsl --install
다운로드 중: Ubuntu
설치 중: Ubuntu
이 배포에 대한 설치, 제거 또는 변환이 진행 중입니다.

오류 코드: Wsl/InstallDistro/Service/RegisterDistro/0x8000000d
```


? 그런디 WSL배포판이 설치가 안되어있는건 아님
```
PS C:\WINDOWS\Logs\DISM> wsl -l -v
  NAME      STATE           VERSION
  Ubuntu    Installing      2
  
PS C:\WINDOWS\Logs\DISM> wsl --version
WSL 버전: 2.5.10.0
커널 버전: 6.6.87.2-1
WSLg 버전: 1.0.66
MSRDC 버전: 1.2.6074
Direct3D 버전: 1.611.1-81528511
DXCore 버전: 10.0.26100.1-240331-1435.ge-release
Windows 버전: 10.0.19045.6332
```


?? 뭐가문제인디?


HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Lxss\
키값도 확인함
![[Pasted image 20250917161036.png]]


뭔디 뭐가문제인디;


ubuntu 가 설치중으로 뜨니까, 삭제하고 다시 깐다
삭제할땐 예외에러도 나옴;
```
PS C:\WINDOWS\Logs\DISM> wsl --unregister Ubuntu

등록 취소 중입니다.

{응용 프로그램 오류} 예외 %s (0x

오류 코드: Wsl/Service/ERROR_UNHANDLED_EXCEPTION
```

근데 또 다시 확인해보면 멀쩡함 ;
```
PS C:\WINDOWS\Logs\DISM> wsl -l -v
Linux용 Windows 하위 시스템 설치된 배포가 없습니다.
아래 지침에 따라 배포를 설치하여 이 resolve 수 있습니다.
  
사용 가능한 배포를 나열하려면 'wsl.exe --list --online' 사용
설치하려면 'wsl.exe --install <Distro>'를 선택하세요.
  

PS C:\WINDOWS\Logs\DISM> wsl.exe --list --online
다음은 설치할 수 있는 유효한 배포 목록입니다.
'wsl.exe --install <Distro>'을 사용하여 설치합니다.
NAME                            FRIENDLY NAME
AlmaLinux-8                     AlmaLinux OS 8
AlmaLinux-9                     AlmaLinux OS 9
AlmaLinux-Kitten-10             AlmaLinux OS Kitten 10
AlmaLinux-10                    AlmaLinux OS 10
Debian                          Debian GNU/Linux
FedoraLinux-42                  Fedora Linux 42
SUSE-Linux-Enterprise-15-SP6    SUSE Linux Enterprise 15 SP6
SUSE-Linux-Enterprise-15-SP7    SUSE Linux Enterprise 15 SP7
Ubuntu                          Ubuntu
Ubuntu-24.04                    Ubuntu 24.04 LTS
archlinux                       Arch Linux
kali-linux                      Kali Linux Rolling
openSUSE-Tumbleweed             openSUSE Tumbleweed
openSUSE-Leap-15.6              openSUSE Leap 15.6
Ubuntu-20.04                    Ubuntu 20.04 LTS
Ubuntu-22.04                    Ubuntu 22.04 LTS
OracleLinux_7_9                 Oracle Linux 7.9
OracleLinux_8_10                Oracle Linux 8.10
OracleLinux_9_5                 Oracle Linux 9.5
```




그래서 다시 깜 
```
 wsl --install -d Ubuntu
```


이번엔 이런 오류로 날 깜
```
PS C:\Windows\System32> wsl --install -d Ubuntu
다운로드 중: Ubuntu
설치 중: Ubuntu
필요한 기능이 설치되어 있지 않기 때문에 작업을 시작할 수 없습니다.
오류 코드: Wsl/InstallDistro/Service/RegisterDistro/CreateVm/HCS/HCS_E_SERVICE_NOT_AVAILABLE
```



그래서 MS store에서 ubuntu 22.04.5 LTS를 다운로드 받아서 바로 실행해보기로함 ㄱㄱ

실행이 또 안됨 답답해서 끄고, 우분투 다시 삭제하고 다시 켜려고하는중

wsl --unregister Ubuntu-22.04
그랬더니 이런 파일이 없다네....

일단 Ubuntu 22.04.5 설치받아서 실행시키니까 아래 에러남
```
Installing, this may take a few minutes...  
WslRegisterDistribution failed with error: 0x80370114  
Error: 0x80370114 ??? ??? ???? ?? ?? ??? ??? ??? ? ????.
```


일단 https://www.lainyzine.com/ko/article/how-to-install-wsl2-and-use-linux-on-windows-10/
이거 따라서 wsl update 하는중....

update도 에러됨 세상이 날 억까하는구만

```
Linux용 Windows 하위 시스템 버전을 2.6.1(으)로 업데이트하는 중입니다.
Service 'WSL Service' (WSLService) could not be stopped.  Verify that you have sufficient privileges to stop system services.
업데이트하지 못했습니다(종료 코드: 1603).
로그 파일: C:\Users\admin\AppData\Local\Temp\wsl-install-logs.txt
오류 코드: Wsl/UpdatePackage/ERROR_INSTALL_FAILURE
```


=> WSL이 좀비상태인것같다고 함. WSL2 기능 다 끄고 껐다켰음 ㄱㄱ 도커도 삭제되어있는 상태~
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
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


질문 : 그래서  windows10 home에서 docker를 설치하려면 필요한 기능이 뭐뭐인데?
-(설치됨) Windows 하이퍼바이저 플랫폼, 가상머신 플랫폼, Linux용 Windows 하위 시스템 



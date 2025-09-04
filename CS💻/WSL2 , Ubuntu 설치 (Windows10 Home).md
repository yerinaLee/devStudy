
지금 문제 : ubuntu 설치할 때 0x80370114 에러 뜨고, download는 되지만 설치가 안된다

일단 Windows 기능에서 하이퍼 어쩌구는 껐음
![[Pasted image 20250904174715.png]]




1) 부팅 구성에 하이퍼바이저 시작이 사용하도록 설정되어 있는지 확인한다. --> Auto로 잘 설정되어 있는 것을 확인했다.

```
bcdedit /enum | findstr -i hypervisorlaunchtype
```

이거 Auto가 아니었고, 바꿔서 Auto 나옴. 재부팅되어야함



참고중인 블로그
https://zooyeonii.tistory.com/93
https://sean.tistory.com/301#google_vignette


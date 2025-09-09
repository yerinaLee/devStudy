특정 상황의 시그널(ex:스크립트 종료, 오류 발생 ..) 을 잡아내, 해당 시그널을 받았을 때 실행할 명령/작업을 정의함

```
trap commands signals
```


ex) 1. 종료 시 정리작업 수행 쉘
```
#!/bin/bash 

# 정리 작업을 위한 함수 정의 

cleanup() { 
	echo "Cleaning up temporary files..." 
	rm -f /tmp/my_temp_file* 
} 

# EXIT 시그널을 받았을 때 cleanup 함수 실행 
trap cleanup EXIT 

# 임시 파일 생성 
touch /tmp/my_temp_file_1 /tmp/my_temp_file_2 
echo "Doing some work..." 
sleep 2
```


쉘이 종료될때마다 cleanup() 실행. 임시파일 삭제됨
결과 : 
```
Doing some work...
Cleaning up temporary files...
```




에러인경우 종료 signal : ERR

|시그널 번호|시그널 이름|설명
0  EXIT   쉘의 종료
1  HUP   터미널이 종료되었을때 발생하는 시그널
2  INT    Del 키를 눌렀을때 발생되는 시그널로 현재 프로그램의 중단의미
3  QUIT   Ctrl + \ 키를 누르면 발생되는 시그널로 현재 프로그램을 종료
9  KILL    프로그램을 강제로 종료시키기 위해서 보내는 시그널로 무시하거나 추적해서 처리할 수 없다.
11 SEGV   segmentation violation 에 발생되는 시그널이다. 유닉스를 프로세스가 사용하는 메모리 영역을 보호하는데, 다른 프로세스가 사용하는 메모리 영역을 침범하려고 할때 주로 발생한다.
15 TERM   이 시그널을 받은 프로세스는 종료가 된다. 기본적인 동작은 KILL 과 같지만 KILL 과는 다르게 무시할 수도 있고, 추적해서 처리할 수도 있다.


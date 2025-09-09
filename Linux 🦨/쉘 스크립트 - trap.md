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



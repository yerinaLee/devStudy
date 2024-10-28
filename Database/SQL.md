
## - SQL JOINS
![](https://t1.daumcdn.net/cfile/tistory/99219C345BE91A7E32)





```
SHOW FULL processlist; -- 현재 세션 목록 확인, State에서 상태 체크

// kill [id입력]  
kill 105621;
```


- 디비버 UI로 하려면?
- DB 우클릭 -> 도구 -> session Manager
- 내 IP 찾아서 상태 체크하고 kill



## - Count
>    - COUNT(\*) : NULL 및 중복 값을 포함하는 행을 포함하여 SELECT 문에 의해 검색된 행을 카운트
>    - COUNT(expression) : 컬럼이 NULL 이 아닌 값을 제외하고 카운트
>    - COUNT(DISTINCT expression) : 컬럼이 NULL이 아닌 UNIQUE(고유)한 값만 카운트







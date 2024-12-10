RU **(Return User)** :  기간 내 인게임 신규 접속 유저
```
select count(*) from daily_active_user dau
where dau.day_created between '20241130' and '20241210'
and dau.last_active is null;
```



ARU (Accumulate Register User): _해당 기간까지의 등록된 누적 유저 수_.

RR(Retention Rate) 지속 사용 유저 비율
UV (순 방문자수, Unique visitor) : **일정기간 내에 게임에 접속한 실제 이용자 수**를 의미한다. 동일 유저가 여러번 방문해도 1로 카운트 하며,
PAU
URR 유저 복귀율 (User Retention Rate

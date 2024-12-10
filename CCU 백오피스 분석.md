RU :  기간 내 인게임 신규 접속 유저
```
select count(*) from daily_active_user dau
where dau.day_created between '20241130' and '20241210'
and dau.last_active is null;
```




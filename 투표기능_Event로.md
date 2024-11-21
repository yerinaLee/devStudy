
Event 테이블과 연동
reward

reward condition 에서 동적으로 메서드가 달라짐
reward_name 이 group_name으로 들어감

vote_item마다 reward를 늘리는 방식

reward_item은 아마 빼도될듯?
reward_item_log


## Event 테이블

Event type 에 vote를 추가 =>  Event 도메인 수정
```
enum Type {  
   GENERAL //GENERAL: general event   
,FLASHSHOP // FLASHSHOP:for flashshop only. Ex:1111 event  
,VOTE
}
```
Start, End date


![[Pasted image 20241121094456.png]]
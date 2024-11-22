
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



## Event에 연결되는 Reward 테이블

reward (vote item)
![[Pasted image 20241122112336.png]]

vote 그룹 별(Event) 투표항목 각각 선정

투표마다 조건식 추가한다면 : reward_condition
http://qa-happycode.mangot5.com:8080/rewardCondition/index

level : 노출 순위
reward_condition : 동적 메서드
reward_condition_params : 동적 메서드 작동시 필요한 파라미터들



test ::: reward_item을 매핑 안해도 log에 쌓이는지?
reward 작동방식 알아야


reward_point_use_history 에 쌓을수있을듯? => 유저 투표결과~~


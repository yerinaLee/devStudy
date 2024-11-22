
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



## Reward 테이블

reward (vote item) : vote 그룹 별(Event) 투표항목 각각 등록
![[Pasted image 20241122112336.png]]

**컬럼 설명**
reward_name : group_name 으로 한 투표이벤트 안에 여러 그룹 설정 가능
level : 노출 순위
reward_condition : 동적 메서드 / 투표 조건이 있는 경우 메서드 검증거침
(백오피스 : http://qa-happycode.mangot5.com:8080/rewardCondition/index)

reward_condition_params : 동적 메서드 작동시 필요한 파라미터들




test ::: reward_item을 매핑 안해도 reward_point_use_history에 쌓이는지?
기존 코드에서 활용할 수 있는 부분들이 어디어디인지 뽑아놓기
reward 작동방식 알아야


user 투표결과 log : reward_point_use_history 에 쌓을수있을듯?
![[Pasted image 20241122113424.png]]



궁금증 : 그럼 유저별 투표횟수는 어떻게 제어하지? => 이렇게 가면 투표페이지 불러올때 하드코딩으로 박아야하나..?
=> reward 테이블의 params가 어떻게 쓰이는지 봐야겠다
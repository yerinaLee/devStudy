클라이언트는 DB 서버에 연결을 네트워크 요청을 하여 TCP/IP 커넥션을 맺는다.

이때, DB 서버는 내부에 session이라는 것을 만드는데, 그리고 앞으로 커넥션을 통한 모든 요청은 이 session을 통해서 실행하게 된다

MySQL 또한 thread 기반으로 동작


## session이란?

Connection은 물리적인 coummunication 채널이고 **session은 client가 SQL 서버에 연결된 시점부터 나가는 시점까지의 시간**을 말한다.

🗨 세션 안에는 여러개의 트랜잭션이 존재할수 있으며(하나 이상의), 일반적으로 데이터베이스는 여러 곳에서 동시에 접근이 가능하기 때문에 많은 세션이 동시에 연결될수 있다.

🗨 세션은 데이터가 변경, 삭제가 확정될때까지 해당 데이터 조작을 **분리처리**함으로써 데이터와 테이블과의 관계를 **보존하는 역할**을 한다.

🗨 특정 세션에서 조작중인 데이터는 **Transaction**이 ⚡️**commit** 되기 전까지 다른 세션에서 조작할 수 없다.



![post-thumbnail](https://velog.velcdn.com/images/amuse/post/612c3211-0851-46b0-b097-e4e8c43f6493/Screen%20Shot%202021-01-14%20at%2012.26.39%20AM.png)




## Transaction

> A transaction is a sequence of one or more SQL operations that are treated as a unit.

**어떠한 하나의 기능을 수행하는 SQL문이라고 생각하면쉽다**. 각 트랜젝션은 외부와 고립된 상태로 수행되며, 만약 **시스템 실패**시 각 트랜젝션은 **성공**과 **실패** 값만 가지게 된다.

**트랜젝션의 개념은 크게 2가지의 근심에서부터 정의되었다.**  
🤔첫번째, 여러 클라이언트들이 데이터베이스에 동시에 접속을 한다면?  
🤔두번째, 만약 데이터 입출력과정에서 시스템이 실패한다면?

이러한 두가지 상황에서부터 데이터를 보존하기위해 위해 ⚡️**ACID** 라는 특성을 가지고 있다.

A: **Atomicity** (원자성)  
C: **Consistency** (일관성)  
I: **Isolation** (고립성)  
D: **Durability** (내구성)



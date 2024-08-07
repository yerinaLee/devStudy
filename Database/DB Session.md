클라이언트는 DB 서버에 연결을 네트워크 요청을 하여 TCP/IP 커넥션을 맺는다.

이때, DB 서버는 내부에 session이라는 것을 만드는데, 그리고 앞으로 커넥션을 통한 모든 요청은 이 session을 통해서 실행하게 된다

MySQL 또한 thread 기반으로 동작


## session이란?

Connection은 물리적인 coummunication 채널이고 **session은 client가 SQL 서버에 연결된 시점부터 나가는 시점까지의 시간**을 말한다.




1. **CF-Connecting-IP**
클라우드플레어에서 실제 클라이언트의 IP 주소를 서버에 전달할 때 사용하는 헤더


2. **X-Forwarded-For(XFF)**
클라이언트 IP 주소 식별
주로 프록시 서버나 로드 밸런서를 사용할경우, 클라이언트의 원래 IP 주소를 전달

`X-Forwarded-For: client_ip, proxy1_ip, proxy2_ip`
여러 프로시를 거칠경우 쉼표로 구분됨


3. **X-Real-IP**
Nginx 같은 리버스 프록시 서버가 클라이언트의 실제 IP를 전달할 때 사용하는 헤더
- 프록시 미설정시 null


3. **Proxy-Client-IP**
일부 프록시 서버(예: WebLogic, Apache mod_proxy)에서 설정할 수 있는 헤더.
잘 사용되지 않음


4. **WL-Proxy-Client-IP**
Oracle WebLogic Server에서 사용하는 헤더


5. **HTTP_CLIENT_IP**
일부 프록시나 클라이언트가 설정하는 사용자 정의 헤더.
특징: 사실상 거의 사용되지 않음.


7. **HTTP_X_FORWARDED_FOR**
X-Forwarded-For와 같은 의미이나, HTTP_ 접두어는 일부 서버 환경에서 사용됨 
(예: PHP에서 헤더를 환경 변수로 받을 때).


8. **remoteAddr**
서버(예: 톰캣, 스프링)가 인식한 직접 연결된 IP 주소.
프록시 서버를 거쳤다면 프록시의 IP 주소일 수 있음

프록시 환경이 없다면 가장 신뢰할 수 있음. 
but 프록시를 거쳤다면 실제 클라이언트 IP는 아님.




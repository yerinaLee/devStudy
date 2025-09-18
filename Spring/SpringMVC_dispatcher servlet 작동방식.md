
SpringMVC
- front controller pattern으로 설계
- front controller = dispatcher servlet

dispatcher servlet
- 요청에 필요한 공통적인 알고리즘 제공
- 실제 동작 : 각각의 적절한 컴포넌트에게 위임



또한 다른 Servlet과 마찬가지로 Java configuration이나 web.xml에 선언하여 매핑되어야 하는데요.???
-- 그럼 web.xml이 약간 최상위 설정파일같은건가..?



### servlet
> 클라이언트의 요청을 처리하고 결과를 반환하는 기술
> - 동적 웹페이지 서버에서 수행되는 소형 프로그램
> - 사용자의 요청은 각각 하나의 스레드로 수행됨

![[Pasted image 20250918134127.png]]


servlet Container
>servlet의 기능에 대한 정의서를 보고 핸들링함
>- 웹서버와 소켓으로 통신
>ex) Tomcat

작동방식
- client 요청 시 web.xml을 기반으로, 요청 URL이 어느 서블릿에 대한 요청인지 탐색
- 해당 서블릿이 메모리에 없는경우 init()으로 생성
- 생성 후 service() 메서드를 통해 요청 응답은 doGet(), doPost()로 나뉘어 response 생성
- 응답완료 후 서블릿 종료 시 destroy()



아 그니까 요청에 대한 소켓을 자동으로 만들어주는건가?
그렇네 ...




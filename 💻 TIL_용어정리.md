
- ## host
> IT에서는 네트워크에 연결되어 있는 컴퓨터들을 호스트(host)라고 칭합니다. 
> 인터넷은 TCP/IP 프로토콜을 이용하여 통신을 하는데, 통신을 하려고 해도 목적지와 출발지가 없으면 어디로 데이터를 보낼지 받을지 모르죠.(현실의 택배 시스템이라고 생각하면 이해가 쉽습니다.) 하지만 이것을 IP라는 약간의 고유한 주소를 통해 정할 수 있습니다. 즉 호스트는 IP주소를 갖는 시스템이라고 말할수 있겠네요. 

IT에서 호스트는 **IP를 가지고 있고 양방향 통신이 가능한 컴퓨터**


## - mRemoteNG (Server Management Tool)

> 작업용 운영체제 환경이 Windows인 경우 Linux/Unix 환경인 서버를 대상으로 작업 시에 원격 로그인하기 불편한 부분이 있습니다. 
>이 때 mRemoteNG를 사용한다면 편리하게 원격 접근이 가능합니다. 
>mRemoteNG는 SSH, RDP, VNC, Telnet 등 다양한 프로토콜을 지원하여 접속 대상 호스트의 OS에 구애받지 않고 접속이 가능합니다.


## - APM (Application Performance Monitering/Management 앱 성능 모니터링)

> 애플리케이션(시스템, 응용 소프트웨어)의 성능과 서비스 안정성을 감시하고 관리하는 솔루션을 말한다. 이러한 솔루션들은 실시간으로 서비스의 상태를 파악할 수 있도록 하며, 제대로 잘 활용한다면 서비스의 이슈를 재빠르게 확인하고 분석할 수 있도록 도움을 준다. 

CPU 사용량, 응답시간, 오류율, 트랜잭션 추적, 가동시간 등을 체크함
- 실제 사용자 모니터링
- 사용자 정의 트랜잭션 프로파일링
- 구성 요소 모니터링
- 인프라 모니터링

![[Pasted image 20240507104413.png]]


## - CDN(Content Delivery Network 컨텐츠 전송 네트워크)

> CDN(Content Delivery Network)은 지리적으로 분산된 서버들을 연결한 네트워크로서 **웹 컨텐츠의 복사본**을 사용자에 가까운 곳에 두거나 동적 컨텐츠(예: 라이브 비디오 피드)의 전달을 활성화하여 웹 성능 및 속도를 향상할 수 있게 합니다.
> 
> CDN은 **Content Delivery Network**(콘텐츠 전송 네트워크)의 약자입니다. 이름에서 알 수 있듯이 CDN은 사용자 위치, 콘텐츠 원본 서버, [에지](https://www.alibabacloud.com/ko/knowledge/what-is-edge-computing?spm=a2c64.12675912.1389603450.1.7b892830Zk6rWh) 서버 위치를 기준으로 콘텐츠(웹페이지, 동영상, 이미지)를 최종 사용자에게 전송할 수 있는 (에지 로케이션 서버라고도 하는) 분산 노드로 구성된 네트워크입니다. **CDN 노드**는 콘텐츠를 캐싱할 수 있는 캐시 기능을 갖추고 있으며 최종 사용자와 가까운 위치에서 사용자에게 콘텐츠를 제공할 수 있습니다. CDN 노드는 CDN 제공업체에 의해 여러 지역에 구축되고 여러 ISP(인터넷 서비스 제공자) 네트워크에 걸쳐 배포될 수 있습니다.


## - CMS(Content Management System 콘텐츠 관리 시스템)

>홈페이지 구성에 기본 틀을 백엔드에서 컨트롤 할 수 있게 설계함  
>회사) Content Type - Content Group - Content Article - Content Media
>
>공공기관, 기업, 대학, 단체 및 협회의 사이트에서 여러개의 서브 사이트를 보유하고 관리 할 때 손쉽게 제작, 관리를 할 수 있는 **웹 사이트 분양 솔루션**
>전문적인 지식이 없어도 웹 사이트 운영 관리자가 손쉽게 운영, 관리할 수 있는 툴을 제공
>Web Editor를 이용한 WISYWIG방식의 자유로운 컨텐츠 관리로 인터넷만 연결되어 있으면 언제 어디서든 시간과 장소의 구애없이 실시간 업데이트 가능



## - SSH(Secure Shell)

> 원격 호스트에 접속하기 위해 사용되는 보안 프로토콜(필수적인 요소)
> 
> 1. **비대칭키 방식** (lv1. 신원확인)
> 서버 또는 사용자가 Key Pair(공개키.pub-개인키.pem)한 쌍) 생성
> 서버가 공개키를 갖고, 사용자가 개인키를 가짐. 공개키의 보안테스트는 한 쌍으로 이루어진 개인키로만 풀 수 있음
> 
> 2. **대칭키 방식** (lv2. 통신 시 정보암호화)
> 비대칭키 방식으로 쌍방 신원 확인 후 통신 과정에서 정보를 암호화하는 방식.
> 한 개의 키만을 사용. 한 개의 키를 서버-사용자가 공유. 
> 공유된 대칭 키를 이용해 정보를 암호화하면, 받은 쪽에서 동일한 대칭 키로 암호를 풀어 정보를 습득하게 됩니다. 정보 교환이 완료되면 교환 당시 썼던 대칭 키는 폐기되고, 나중에 다시 접속할 때마다 새로운 대칭 키를 생성하여 사용하게 됩니다. (일회용품너낌쓰)



## - War파일(WebAppication Archive)

> 자바 서버 페이지, 자바 서블릿, 정적 웹 페이지 및 웹 애플리케이션을 함께 이루는 기타 자원을 한데 모아 배포하는데 사용되는 Jar파일이다.
> 
> 쉽게 해석하면 배포를 하기 위한 웹 애플리케이션 자원들의 "압축 파일"이라는 뜻이다.


## -jar 파일(Java Archive)

> Java 클래스 파일과 관련 라이브러리, 및 메타데이터를 하나의 파일로 모아서 압축한 파일이다.
> JRE만 있다면 프로젝트 구동이 가능하다.


## - CSP (Cloud Service Provider, 클라우드 서비스 공급자)

 > **개념**
 > - 자체 데이터센터에 보유한 가상화 서버, 네트워크, 상면 등 IT 서비스 운영에 필요한 인프라 및 솔루션 전반을 콘솔로 제공
 > - 퍼블릭 클라우드, 프라이빗 클라우드, 하이브리드 클라우드 등 다양한 클라우드 인프라 구축하여 제공
 >  
 > **예시**
 > - (해외) AWS, MS Azure, GCP 등
 > - (국내)  NHN 클라우드, 네이버 클라우드, KT 클라우드 등


## - L4/L7 로드밸런싱

#### 💡 L4 로드 밸런서 정의

> **L4 로드 밸런서는 전송 계층(Transport Layer, Layer 4)** 에서 작동하는 로드 밸런서로, 주로 TCP 및 UDP 프로토콜을 기반으로 클라이언트와 서버 간의 트래픽을 분산시킵니다. L4 로드 밸런서는 클라이언트의 IP 주소와 포트, 서버의 IP 주소와 포트를 기반으로 로드 밸런싱을 수행합니다.

#### 💡 L7 로드 밸런서 정의

> **L7 로드 밸런서는 애플리케이션 계층(Application Layer, Layer 7)** 에서 작동하는 로드 밸런서로, 주로 HTTP 및 HTTPS 프로토콜을 기반으로 클라이언트와 서버 간의 트래픽을 분산시킵니다. L7 로드 밸런서는 요청 내용(URL, 헤더, 쿠키 등)을 기반으로 로드 밸런싱을 수행합니다.

> [!tip]
> 예를 들어, 실시간 트래픽 처리가 중요한 서비스의 경우 L4 로드 밸런서를 사용하여 빠른 응답 시간을 제공할 수 있으며, 애플리케이션 레벨의 로드 밸런싱이 필요한 서비스에서는 L7 로드 밸런서를 사용하여 다양한 기능과 유연성을 활용할 수 있습니다.


## - 로드 밸런서

> 트래픽을 받아서 **여러 대의 서버에 분산**시키는 하드웨어 또는 소프트웨어
> 
> 클라이언트와 서버 그룹 사이에 위치해 서버에 가해지는 트래픽을 여러 대의 서버에 고르게 분배하여 특정 서버의 부하를 덜어줍니다. 서버가 하나인데 많은 트래픽이 몰릴 경우 부하를 감당하지 못하고, 서버가 다운되어 서비스가 작동을 멈출 수 있습니다.
> 
> L4부터 Port를 다룰 수 있기 때문에 부하 분산에 L4 Load Balancer와 L7 Load Balancer가 많이 사용됩니다. Load Balancer는 한 대 서버의 각각의 포트에 여러개의 서비스들을 운영할 수 있도록 합니다.

![](https://filesystem.cafe24.com/hosting/cloud_service/2021/05/11/b40ba4883297c5999d81cf0e192a6ad4_1620719530.jpg)



---


## - @SuppressWarnings

 **@SuppressWarnings** 어노테이션은 컴파일 경고를 사용하지 않도록 설정해주는 것으로 한마디로 이클립스에서 노란색 표시줄이 나타내는 것 즉, 경고를 제외 시킬 때 사용한다.
 
 > [!note] @SuppressWarnings("unchecked")
> - `@SuppressWarnings("unchecked")`은 미확인 오퍼레이션과 관련된 경고를 억제한다.

 참고 : [IBM문서](https://www.ibm.com/docs/ko/radfws/95?topic=SSRTLW_9.5.0/org.eclipse.jdt.doc.user/tasks/task-suppress_warnings.html)



## - @Resource

> **@Autowired 어노테이션이 타입을 이용해서 의존성을 주입한다면, @Resource 어노테이션은 빈 이름을 이용해서 의존성을 주입한다.**

**@Autowired와 @Resource의 차이점**

1. @Autowired : 타입(클래스)로 Bean을 지정한다.(생성자/필드/메서드에 모두 적용 가능)
2. **@Resource : Name으로 Bean을 지정한다.(필드/메서드에만 적용 가능)**


**예시 코드**

```
@Repository
public class CommonDao {
    @Autowired
    private SqlSessionTemplate sqlSession;
}
```

위와 같이 Autowired를 사용한다면, sqlSession은 SqlSessionTemplate 클래스에 의존성을 가지게 된다.

```
@Repository
public class TestDao {
    @Resource(name="BlueSqlSessionTemplate")
    private SqlSessionTemplate sqlSession;
 }
```

위와 같이 Resource를 사용한다면, sqlSession은 BlueSqlSessionTemplate의 이름을 가진 Bean 객체에 의존성을 가지게 된다.

name 속성을 생략하면, @Resource 어노테이션이 적용된 필드나 설정 메서드의 타입을 사용한다.


---

## - 캐시 Cache

> 자주 사용하는 데이터나 값을 미리 복사해 놓는 임시 장소. 캐시는 저장 공간이 작고 비용이 비싼 대신 빠른 성능을 제공한다.cache
> 
> - 접근 시간에 비해 원래 데이터를 접근하는 시간이 오래 걸리는 경우(서버의 균일한 API 데이터)
> - 반복적으로 동일한 결과를 돌려주는 경우(이미지나 썸네일 등)
>  
> - Cache에 데이터를 미리 복사해 놓으면 계산이나 접근 시간 없이 더 빠른 속도로 데이터에 접근할 수 있다. 결국 **Cache란 반복적으로 데이터를 불러오는 경우에, 지속적으로 DBMS 혹은 서버에 요청하는 것이 아니라 Memory에 데이터를 저장하였다가 불러다 쓰는 것을 의미**한다.


## - Redis
> in-memory 기반의 NoSQL로, key-value의 데이터 구조를 사용하는 데이터베이스
 - redis는 오픈소스로서 데이터베이스(NOSQL DBMS)로 분류가 되기도 하고 Memcached와 같이 인메모리 솔루션으로 분류되기도 한다.

## - Memcached
 >무료로 사용할 수 있는 오픈소스이며 분산 메모리 캐싱 시스템
 >결과 데이터를 작은 단위의 key - value 형태로 메모리에 저장하는 방식
### [참고 : Memcached, Redis](https://brownbears.tistory.com/43)


## -WAS / 웹서버

## **💡 웹 서버**

> **사전적 정의 "웹 브라우저 클라이언트로부터 HTTP 요청을 받아들이고 HTML 문서와 같은 웹 페이지를 반환하는 컴퓨터 프로그램"**

웹 서버란 클라이언트(사용자)가 웹 브라우저에서 어떠한 페이지 요청을 하면 웹 서버에서 그 요청을 받아 **정적 컨텐츠를 제공하는 서버**이다.  여기서 정적 컨텐츠란 **단순 HTML 문서, CSS, javascript, 이미지, 파일 등 즉시 응답가능한 컨텐츠**이다. 그렇다면 웹 서버는 정적 컨텐츠만 제공하느냐? 그것은 아니다. 웹 서버가 동적 컨텐츠를 요청 받으면 WAS에게 해당 요청을 넘겨주고, WAS에서 처리한 결과를 클라이언트(사용자)에게 전달해주는 역할도 한다.

**** 대표적인 웹 서버 : Apache** 

![](https://blog.kakaocdn.net/dn/pxLJe/btqBTL7f4OE/O54n7FkOZUKAItvIPUpwGK/img.png)

▲ 웹 서버 사용자 요청 처리 과정

## 💡 WAS (Web Application Server)

> **사전적 정의  
> "인터넷 상에서 HTTP 프로토콜을 통해 사용자 컴퓨터나 장치에 애플리케이션을 수행해주는 미들웨어로서, 주로 동적 서버 컨텐츠를 수행하는 것으로 웹 서버와 구별이 되며, 주로 데이터베이스 서버와 같이 수행"**

WAS는 웹 서버와 웹 컨테이너가 합쳐진 형태로서, 웹 서버 단독으로는 처리할 수 없는 **데이터베이스의 조회나 다양한 로직 처리가 필요한 동적 컨텐츠를 제공**한다. 덕분에 사용자의 다양한 요구에 맞춰 웹 서비스를 제공할 수 있다. WAS는 **JSP, Servlet 구동환경을 제공**해주기 때문에 웹 컨테이너 혹은 서블릿 컨테이너라고도 불린다. 

**** 대표적인 WAS 종류 : Tomcat**

**** 웹 컨테이너 : 웹 서버가 보낸 JSP, PHP 등의 파일을 수행한 결과를 다시 웹 서버로 보내주는 역할을 함**

![](https://blog.kakaocdn.net/dn/pAqij/btqBS7bDSam/GJDanZaV3kMKPqfXtlEqL0/img.png)

▲ WAS 사용자 요청 처리 과정

[참고링크](https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html)



## - WEB API

> 웹 서버 또는 웹 브라우저를 위한 애플리케이션 프로그래밍 인터페이스이다. HTTP 서비스이고 다양한 클라이언트에서 접근이 가능하도록 설계되어있다. Web 환경을 통해 제공되는 데이터 CRUD인터페이스를 제공한다.

![](https://blog.kakaocdn.net/dn/LSsUR/btqJMw21syp/bo1vHeeHuuJ9tM765Xgmd1/img.png)

  HTTP 표준 접근 방식을 이용하며 플랫폼 환경, 클라이언트 환경의 제한이 없는 서비스 구현이 가능하다.



## - IDC(Internet Data Center / 인터넷 데이터 센터)

> 인터넷 연결의 핵심이 되는 서버를 한 데 모아 집중시킬 필요가 있을 때 설립하는 시설
> IDC를 통해 온라인 게임의 운영에 필요한 서버 컴퓨터(Server Computer)와 네트워크(Network) 회선 등을 제공하는데, 다른 말로는 서버 호텔(Server Hotel)이라고도 부른다.


## - Purge[​](https://docs.kakaocloud.com/service/bns/cdn/cdn-main#purge "Purge에 대한 직접 링크")

>**Purge는 캐시 서버에 저장되어 있는 콘텐츠를 삭제한 후 재배포하는 기능**입니다. 오리진 서버에서 복사되어 캐시 서버에 저장되어 있는 콘텐츠는 캐시 설정 정책에 따라 캐시 서버 보관 시간이 만료되기 전까지 유지됩니다. 캐시 서버 보관 시간이 만료되기 전에 오리진 서버의 파일을 변경하여 배포할 경우, Purge 기능을 사용합니다. Purge 기능을 사용하면 캐시 서버에 저장되어 있던 구 버전의 콘텐츠는 삭제하고, 오리진 서버로부터 새로 변경한 콘텐츠를 받아와 캐시 서버에 최신화된 콘텐츠로 갱신할 수 있습니다.

출처 : [카카오클라우드](https://docs.kakaocloud.com/service/bns/cdn/cdn-main#purge)



## - Model, ModelAndView

> **Model**은 **파라미터 방식**으로 메소드에 **(Model model) 파라미터**를 넣어주고 **String형태로 리턴** / **값을 넣을 때 addAttribute()를 사용**
> 
> **ModelAndView**는 **컴포넌트 방식**으로 **ModelAndView 객체를 생성**해서 **객체형태로 리턴**
> Model과 View를 합쳐놓은 것
> 값을 넣을때 addObject()를 사용하고, **setViewName()**로 보낼 곳 View 세팅한다

[코드 예시](https://develop-im.tistory.com/10)
### [spring 공식문서](https://docs.spring.io/spring-framework/docs/current/javadoc-api/org/springframework/web/servlet/ModelAndView.html)


## - CCU (Concurrent connected User, 동시 접속자)
 동일한 시간대에 게임 서버에 접속한 사람 수
## - DAU (Daily active users, 일일활성유저)
24시간 동안 앱을 사용하는 순 유저 수
## - MCU
 다른 약어로는 PCCU이다.
 가장 많은 사람이 동시에 접속한 특정 시기를 기준으로 게임 서버에 접속한 사람 수

## - VO (Value Object)
> DTO와 비슷하나, **내부 속성 값을 변경할 수 없는(immutable), Read-Only의 의미적 특성을 가진 객체**를 **VO**라 한다. 변경없이 값으로 취급할 객체를 말한다.


## -VPC(Virtual Private Cloud)
> **퍼블릭 클라우드 환경에서 사용할 수 있는 고객 전용 사설 네트워크**
> 다른 네트워크와 논리적으로 분리되어 있어 IT 인프라를 안전하게 구축하고 간편하게 관리할 수 있습니다.

## EC2 ( Elastic Compute Cloud) 란

- **아마존 웹 서비스(AWS)에서 제공하는 클라우드 컴퓨팅 서비스**
- 클라우드 컴퓨팅은 인터넷(클라우드)을 통해 서버, 스토리지, 데이터베이스 등의 컴퓨팅 서비스를 제공 → **AWS에서 원격으로 제어할 수 있는 가상의 컴퓨터를 한 대 빌리는 것**
- 후불제 PC방과 같이 **사용한 만큼 비용을 지불**하기 때문에 탄력적인 이라는 의미의 **Elastic**이라는 단어가 붙어있다. Elastic은 **비용**적인 부분 뿐만이 아니라 필요에 따라 **성능, 용량**을 자유롭게 조절할 수 있다는 의미도 가지고 있다

> 📌 **정리 : EC2서비스는 AWS에서 비용, 성능, 용량면에서 탄력적인 클라우드 컴퓨터를 제공하는 서비스라고 할 수 있다**


## recaptcha (google)

> 컴퓨터 봇에 의한 스팸, [해킹](https://namu.wiki/w/%ED%95%B4%ED%82%B9 "해킹") 등을 방지하기 위해 개발한 테스트인 [CAPTCHA](https://namu.wiki/w/CAPTCHA "CAPTCHA")의 후속 버전.  reCAPTCHA는 [구글](https://namu.wiki/w/%EA%B5%AC%EA%B8%80 "구글")에서 제공하는 봇 방지 API로, 최신 버전은 v2이며 v3의 베타 버전이 나와있다.
> ![[Pasted image 20240520174820.png]]


## - Proxy
> ![](https://velog.velcdn.com/images/younghyun/post/6f259bc2-6851-406e-a086-7b8eb90ba0b1/image.png)- 클라이언트와 서버 사이에 존재하며, 중계기로서 대리로 통신을 수행하는 것을 `Proxy`라고 하며, 그 중계 기능을 하는 주체를 `Proxy Server`라고 한다.
> 
> **포워드 프록시(Forward Proxy)**
> 보통 말하는 프록시. Client와 Server 사이에 위치하여 요청을 중계하며, 요청과 응답은 Proxy Server를 거침  / **클라이언트를 감추는 효과**
> ![](https://velog.velcdn.com/images/younghyun/post/8a3571b5-9c48-4523-95fe-3bd1815e1392/image.png)


## - ObjectMapper
> JSON 문자열과 Java 객체 간의 변환을 담당
> Spring에서는 기본적으로 jackson 모듈의 ObjectMapper라는 클래스가 직렬화를 처리한다.


## - .gsp 파일
> `.gsp` 파일은 Grails 애플리케이션에서 사용되는 파일 형식
> GSP는 "Groovy Server Pages"의 약자로, Grails 프레임워크에서 JSP(JavaServer Pages)와 유사한 역할을 수행. HTML과 Groovy 코드를 결합하여 동적 웹 페이지를 생성하는 데 사용. Grails의 MVC(Model-View-Controller) 패턴에서 View 역할


## - Tomcat, Catalina 카탈리나
> 아파치 소프트웨어 재단(ASF)의 오픈 소스 자바 서블릿 컨테이너
> 서블릿, JSP, EL, JSTL, WebSocket 등 여러가지 JavaEE 기술을 구현하고, Java 코드를 실행하는 순수 Java Http 웹 서버이다.(쉽게 말해서 자바 웹 서버)
>
>**톰캣 카탈리나(Catalina)**
>톰캣은 여러개의 기능(부품)으로 구성한다. 톰캣의 코어 컴포넌트는 카탈리나라고 칭한다.
>카탈리나는 톰캣의 서블릿 스펙의 실질적인 구동을 제공한다. 톰캣 서버를 가동시킬 경우, 카탈리나를 구동시킨 것이라고 생각하면 된다. **카탈리나 기본동작은 톰캣의 6개 config 파일을 편집하여 구현/제어** 할 수 있다.
>
> **cataline.policy**
>- JavaEE 스펙에 정의된 표준 보안 정책 구문으로 표현된 카탈리나 자바 클래스의 톰캣 보안 정책이다. 톰캣의 코어 보안 정책, 시스템 코드, 웹앱, 카탈리나 자체의 permission(사용권한)이 정의되어 있다.
>- 
> **catalina.properties**
> - 클래스를 위한 표준 자바 프로퍼티. 보안 패키지 리스트, 클래스 로더 패스 등과 같은 정보. 톰캣의 성능 최적화를 위한 String 캐시 설정이 포함됨
> 
> **logging.properties**
> - 이 파일은 임계값, 로그값의 위치와 같은 카탈리나의 로깅 기능을 구성하는 방법이다. 로그의 모든 항목은 JDK의 로깅 구현 대신, 톰캣이 자동으로 사용하는 commons-logging 구현인 JULI 참조한다.
> 
> **context.xml**
> - 이 파일은 톰캣에 구동되는 웹앱에 대해 로드될 정보들이다.
> 
> **server.xml**
> - 톰캣의 메인 config 파일이다. 자바 서블릿 스펙에 지정된 계층적 문법을 사용하여, 카탈리나의 초기 상태 구성, 톰캣을 부팅하고 구성 요소의 빌드 순서를 정의한다. 이 xml 파일은 복잡하지만 자세한 것은 아파치 홈페이지에서 확인하자.
> 
> **tomcat-users.xml**
> - 톰캣 서버의 많은 유저, 패스워드, 유저롤(role)에 관한 정보와 데이터에 엑세스하는 신뢰된 영역(JNDI, JDBC 등) 에 대한 정보가 들어있다.
> 
> **web.xml**
> - 버퍼 크기, 디버깅 레벨, 클래스패스와 같은 Jasper 옵션, MIME 유형 및 웹페이지 index 파일 같은 서블릿 정의를 포함하여, 톰캣 인스턴스에 로드되는 모든 응용 프로그램에 적용하는 옵션 또는 값이다.
> 
> **재스퍼(Jasper)**
> - 톰캣의 JSP 엔진이다. 제스퍼는 JSP 파일을 파싱하여 서블릿(JavaEE) 코드로 컴파일한다. JSP 파일의 변경을 감지하여 리컴파일 작업도 수행한다.

## - Apache Zeppelin이란?
> Spark에 데이터 탐색,시각화, 공유 및 협업 기능을 제공하는 web기반의 notebook입니다.
> Spark : Apache  Spark는 빅 데이터 워크로드에 사용되는 오픈 소스 분산 처리 시스템

## - OTP
> OTP의 뜻은 **One Time Password**, 같은 시간에 생겨난 비밀번호예요. 인증이 필요한 순간에, 고객의 OTP와 은행 서버에서 동시에 6자리의 랜덤 숫자를 만들고 이 숫자가 맞는지 확인하죠.

## - AuthKey, 플랫폼 인증키
> 런처실행시 사용하는키(외부노출키)
> : 유저 인증시 사용: 사용자 웹로그인(아이디로그인) 완료이후 사용자 인증용으로 사용

## - tokken key
> 조합된 비공개키-외부에 공개하지 않음
>  : 로그인 연동처리시 사용

## - SSL (Secure Sockets Layer, 보안 소켓 계층)
> 웹사이트와 브라우저 사이(또는 두 서버 사이)에 전송되는 데이터를 암호화하여 인터넷 연결을 보호하기 위한 표준 기술

## - SSL 관련 문제 해결(서버 인증서)

## - OBT(Open Beta test), CBT(Close Beta Test)
> CBT : 비공개테스트 / 게임 오픈하기전에 일부 유저들을 뽑아서 비공개 테스트를 진행한다
> OBT : 공개테스트 / 서버를 오픈해서 공개 테스트 하는것이며, 말 그대로 모든 유저가 할 수 있다.

## - N/A
> not applicable 또는 not available의 두문자어로 "해당사항 없음"을 의미한다.

## - Ping (Paket Internet Groper)
핑.ᐟ하ヱ 불나와 ના너ના너スΙ ⌝ᥣ모ටㅏ ටㅏ주발⋌˫퐈.ᐟ.ᐟ
> 컴퓨터 네트워크 상태를 점검, 진단하는 명령어
> ping을 보내는 대상 컴퓨터를 향해 일정 크기의 패킷(packet, 네트워크 최소 전송 단위)을 보낸 후  (ICMP echo request) 대상 컴퓨터가 이에 ping에 대해 응답하는 메시지(ICMP echo reply)를 보내면 이를 수신, 분석하여 대상 컴퓨터가 작동하는지, 또는 대상 컴퓨터까지 도달하는 네트워크 상태는 어떠한지를 알 수 있다.
> 참고 : https://velog.io/@gaheekim610/Ping%EA%B0%9C%EB%85%90
> 
> TTL Linux = 64 / Windows = 128 / Cisco = 256
> **TTL 값은 Time-To-Live** 라는 값으로 장비를 거치면서(홉) TTL 값을 하나씩 감소시키고 TTL 값이 0이 되게 되면 패킷을 드롭하게 됩니다.


## - 네트워크 대역폭
> **일정 시간 동안 전송 가능한 데이터의 양**입니다. 즉, 네트워크의 최대 전송 속도입니다. 만약 네트워크 대역폭이 10Mbps라면 초당 1.25MB(10Mb)의 데이터를 보낼 수 있는 전송 속도를 의미합니다.


### - 직렬화(Serialization) /  역직렬화(Deserialization)
> ✅ **직렬화** : 객체들의 데이터를 연속적인 데이터(스트림 / (Byte,CSV,Json..))로 변형하여 전송 가능한 형태로 만드는 것
> 
> ✅ **역직렬화** : 직렬화된 데이터를 다시 객체의 형태로 만드는 것 / 포멧(Byte,CSV,Json..) 형태에서 객체로 변환하는 과정


## - VMSS (Virtual Machine Scale Sets)

> VMSS는 "Virtual Machine Scale Sets"의 약자로, 마이크로소프트 애저(Azure) 클라우드 플랫폼에서 제공하는 서비스입니다. 이 서비스는 동일한 가상머신(VM) 설정을 기반으로 자동으로 수평 확장 및 축소를 관리할 수 있게 해줍니다. 즉, 애플리케이션의 수요에 따라 자동으로 VM 인스턴스의 수를 늘리거나 줄일 수 있습니다.


## - curl 명령어
> curl(client url) 명령어는 **프로토콜들을 이용해 URL로 데이터를 전송해 서버에 데이터를 보내거나 가져올 때 사용하기 위한 명령줄 도구 및 라이브러리**입니다.

> curl(client url) 명령어는 프로토콜들을 이용해 **URL 로 데이터를 전송**하여 **서버에 데이터를 보내거나 가져올때** 사용하기 위한 명령줄 도구 및 라이브러리이다. 쉽게말해 예를들어 자바스크립트 환경에서 REST API(http)를 테스트하고싶다면 보통 ajax, fetch 를 이용해 요청을 보내는 것과 같이, **SHELL(커맨드라인 환경)에서 REST API(http) 테스트 하고 싶으면 curl 명령어를 이용**하면 된다 라고 이해하면 된다.

[LINUX-📚-CURL-명령어-사용법-다양한-예제로-정리](https://inpa.tistory.com/entry/LINUX-%F0%9F%93%9A-CURL-%EB%AA%85%EB%A0%B9%EC%96%B4-%EC%82%AC%EC%9A%A9%EB%B2%95-%EB%8B%A4%EC%96%91%ED%95%9C-%EC%98%88%EC%A0%9C%EB%A1%9C-%EC%A0%95%EB%A6%AC)


## - VM (가상 머신 / Virtual Machine) 
> 가상 머신은 물리적 하드웨어 시스템에 설치된 소프트웨어나 운영 체제 위에서 가상으로 구현된 컴퓨터 시스템을 의미합니다. 즉, 실제 물리적 컴퓨터 없이도 컴퓨터 환경을 소프트웨어로 구현하여 사용할 수 있게 해줍니다.

## - tomcat Connection
> 톰캣에서는 **socket과 SocketWrapper를 합해 connection이라 간주**하고 있습니다.

## - server scale out, scale up
> 서버의 "Scale Out"이란 시스템의 처리 능력을 향상시키기 위해 동일한 기능을 하는 서버를 추가로 배치하는 확장 방식을 말합니다. 이 방식은 "수평 확장"이라고도 불리며, 반대 개념으로는 한 대의 서버의 성능을 높이는 "Scale Up" 또는 "수직 확장"이 있습니다.
>
>Scale Out의 주요 특징은 다음과 같습니다:
>
>1. **탄력성**: 트래픽이나 처리해야 할 작업량이 증가할 때 쉽게 서버를 추가하여 시스템 전체의 처리 능력을 높일 수 있습니다.
>2. **고가용성**: 여러 대의 서버가 동일한 작업을 처리하기 때문에, 한 대 이상의 서버에 문제가 생겨도 시스템 전체가 멈추지 않고 서비스를 지속할 수 있습니다.
>3. **비용 효율성**: 초기 비용이 비교적 낮고, 필요에 따라 점진적으로 확장할 수 있어 장기적으로 비용 효율이 좋을 수 있습니다.
>
>Scale Out은 주로 웹 서비스, 데이터베이스, 분산 처리 시스템 등 다양한 분야에서 사용되며, 클라우드 컴퓨팅 환경에서 특히 유용합니다. 클라우드 서비스는 사용자가 손쉽게 서버를 추가하고 관리할 수 있는 기능을 제공하기 때문에, 필요에 따라 신속하게 시스템을 확장할 수 있습니다.

![](https://blog.kakaocdn.net/dn/AiIza/btrsMXnwf6v/2tmcajq08uJokSM1VmnbX1/img.png)

## - Jedis
> Redis를 자바에서 쉽게 사용할 수 있게 도와주는 라이브러리

## - XLog(응답 분포 차트)

## - idle thread 유휴 스레드


## - 엔드포인트

> 엔드포인트는 **컴퓨터 네트워크에 연결하고 컴퓨터 네트워크와 정보를 교환하는 물리적 디바이스**입니다. 엔드포인트의 몇 가지 예를 들면 모바일 디바이스, 데스크톱 컴퓨터, 가상 머신, 임베디드 디바이스, 서버가 있습니다.


## - 프로시저(Procedure)

> 프로시저는 **특정 작업을 수행하기 위해 미리 정의된 코드 블록**입니다. 주로 데이터베이스 시스템에서 사용되며, 저장 프로시저라고도 합니다.
> 데이터베이스에 대한 일련의 작업을 정리한 절차를 관계형 데이터베이스 관리 시스템에 저장한 것으로 영구저장모듈(Persistent Storage Module)이라고도 불립니다.
> 
> 보통 저장 프로시저를 프로시저라고 부르며, 일련의 쿼리를 마치 하나의 함수처럼 실행하기 위한 쿼리의 집합입니다.
> 
> 즉, 특정 작업을 위한 쿼리들의 블록입니다.


## - TPS (Transaction Per Second / 초당 트랜잭션 개수)
> 실제 계산하는 방식은 일정 기간 동안 실행된 트랜잭션의 개수를 구하고 다시 1초 구간에 대한 값으로 변경


## - 레지스트리
> **운영 체제의 설정 및 정보까지 담고 있는 데이터베이스**
> 1. **구성 요소**:    
    - **키(Key)**: 폴더와 유사한 구조로, 레지스트리는 여러 개의 키로 구성됩니다. 각 키는 하위 키를 가질 수 있습니다.
    - **값(Value)**: 각 키는 하나 이상의 값을 가질 수 있으며, 값은 특정 설정이나 정보를 저장합니다. 값은 이름, 데이터 유형, 실제 데이터로 구성됩니다.
>
>1. **주요 루트 키**:   
    - **HKEY_CLASSES_ROOT (HKCR)**: 파일 확장자와 관련된 정보 및 파일 형식과 응용 프로그램 간의 연결 정보를 저장합니다.
    - **HKEY_CURRENT_USER (HKCU)**: 현재 로그인한 사용자와 관련된 설정 정보를 저장합니다.
    - **HKEY_LOCAL_MACHINE (HKLM)**: 시스템 전체에 적용되는 설정 정보를 저장합니다.
    - **HKEY_USERS (HKU)**: 컴퓨터에 있는 모든 사용자 계정의 설정 정보를 저장합니다.
    - **HKEY_CURRENT_CONFIG (HKCC)**: 현재 하드웨어 프로파일에 대한 설정 정보를 저장합니다.


## - shard
> 같은 테이블 스키마를 가진 데이터를 다수의 데이터베이스에 분산하여 저장하는 방법을 의미합니다.
> [![No Image](https://nesoy.github.io/assets/posts/20180222/5.png)](https://nesoy.github.io/assets/posts/20180222/5.png)


## - 람다식
> 메서드를 **"하나의 식"으로 표현**한 것. 하나의 식으로 표현하여 훨씬 간략하게 표현이 가능하게 되며, 메서드의 이름과 반환값이 없어지므로 **"익명함수"**라고도 함
> ![etc-image-2](https://blog.kakaocdn.net/dn/bM8mak/btrR9MXmHXJ/j6KQhGmmiOH8gS4PqXpsVk/img.png)

## - 자바 스트림(Stream)
> Java 8부터 추가된 기술로 람다를 활용해 배열과 컬렉션을 함수형으로 간단하게 처리할 수 있는 기술이다.

## - 트래픽
> - 트래픽이란 서버를 통해 최종 사용자에게 전달된 데이터의 양을 말합니다.
> - 단위 일반적으로 바이트단위로 (KBytes, MegaBytes, GigaBytes 등등) 표현합니다.    
    트래픽 = 용량 * 사용자 수 * 개수 
    ex) 4GB 영화 * 10명 * 10개 = 400GB

## - CI/CD
> 1. **CI (Continuous Integration, 지속적 통합)**:    
    - 개발자들이 작성한 코드를 정기적으로(보통 하루에 여러 번) 중앙 저장소에 병합하는 프로세스입니다.
    - 각 병합마다 자동화된 빌드와 테스트가 실행되어 코드의 품질을 유지하고, 통합 과정에서 발생할 수 있는 문제를 조기에 발견하게 합니다.
 2. **CD (Continuous Delivery, 지속적 전달) 또는 Continuous Deployment (지속적 배포)**:
>	- **지속적 전달**: 중앙 저장소에 병합된 코드가 자동으로 배포 준비 상태까지 진행되는 프로세스입니다. 이는 테스트 환경이나 프로덕션 환경에 배포할 준비가 된 상태를 의미합니다. 배포는 여전히 수동으로 이루어질 수 있습니다.
	 - **지속적 배포**: 중앙 저장소에 병합된 코드가 자동으로 프로덕션 환경에 배포되는 프로세스입니다. 이는 완전 자동화된 배포 프로세스이며, 실제 사용자에게 코드가 배포되는 과정을 포함합니다.
   CI/CD는 소프트웨어 개발 및 배포의 효율성을 높이고, 코드 변경 사항이 빠르고 안전하게 사용자에게 전달될 수 있도록 도와줍니다. 이를 통해 개발자는 더 자주, 더 안정적으로 소프트웨어를 릴리스할 수 있습니다.


## - DevOps
> "Development" (개발)과 "Operations" (운영)의 합성어로, 소프트웨어 개발과 운영의 협력과 통합을 강조하는 문화, 운동, 또는 관행입니다. 이 개념의 핵심은 개발팀과 운영팀 간의 장벽을 허물고, 더 빠르고 효율적으로 소프트웨어를 개발하고 배포하는 것입니다. DevOps는 CI/CD와 같은 자동화된 프로세스를 중요시하며, 더 나은 품질의 소프트웨어를 더 빠르게 사용자에게 제공하기 위해 지속적인 피드백과 개선을 추구합니다.

## - OAuth
> 프로토콜임. 인터넷 사용자들이 비밀번호를 제공하지 않고 다른 웹사이트 상의 자신들의 정보에 대해 웹사이트나 애플리케이션의 접근 권한을 부여할 수 있는 공통적인 수단으로서 사용되는, 접근 위임을 위한 개방형 표준이다.
> [![OAuth-20img.png)](https://blog.kakaocdn.net/dn/bHUGoo/btrm2orrAFu/CPLsbvhQnELKQEukKU7jX1/img.png)
>  요런거!
>  OAuth 2.0은 1.0에서 알려진 보안 문제 등을 개선한 버젼이다.


## - HMAC-SHA1
> 메시지 인증 코드(Message Authentication Code, MAC)의 한 형태로, 해시 기반 메시지 인증 코드(Hash-based Message Authentication Code, HMAC)와 SHA-1(Secure Hash Algorithm 1)을 결합한 것입니다. 이를 통해 데이터의 무결성과 인증을 보장할 수 있습니다.

## - HMAC-MD5
> HMAC(Hash-based Message Authentication Code)와 MD5(Message Digest Algorithm 5)를 결합한 메시지 인증 코드
> 
> HMAC-MD5는 과거에 널리 사용되었으나, MD5 해시 함수 자체의 보안 취약점 때문에 현재는 더 안전한 해시 함수(HMAC-SHA256 등)를 사용하는 것이 권장됩니다. MD5는 충돌 공격에 취약하여 데이터의 무결성을 완벽하게 보장하지 못할 수 있으므로, 보안이 중요한 응용 프로그램에서는 사용을 피해야 합니다.

## - bash
> Bash(Bourne Again SHell)는 유닉스와 리눅스 운영 체제에서 널리 사용되는 쉘(Shell)입니다. 쉘은 사용자와 운영 체제 사이의 명령어 인터페이스로, 사용자가 명령어를 입력하면 이를 해석하고 실행해주는 역할을 합니다. Bash는 GNU 프로젝트의 일환으로 개발되었으며, `sh` (Bourne Shell)를 대체하기 위해 만들어졌습니다.


## - 아이프레임 iframe
> HTML Inline Frame 요소이며 **inline frame의 약자**이다. 
> 효과적으로 **다른 HTML 페이지를 현재 페이지에 포함**시키는 중첩된 브라우저로  
> iframe 요소를 이용하면 해당 웹 페이지 안에 어떠한 제한 없이 **다른 페이지를 불러와서 삽입** 할 수 있다.  

## - 도메인 중심 개발 Domain Driven Design
> 개발을 함에 있어 위에서 설명한 도메인이 중심이 되는 개발 방식
> 도메인 엔티티 정의 -> 리파지토리, 서비스, 스프링 빈 구성


## - SDK (Software Development Kit)
> 소프트웨어 개발 도구 모음.
> 개발 도구 프로그램, 디버깅 프로그램, 문서, API 등이 있다.

## - telnet
> `telnet`은 네트워크 프로토콜 중 하나로, TCP/IP 네트워크를 통해 다른 컴퓨터에 접속하여 명령어를 실행할 수 있게 해줍니다. 주로 원격 서버에 접속하거나 네트워크 서비스를 테스트하는 데 사용됩니다.
```
 telnet [호스트] [포트]
```

## - PL/SQL (Procedural Language extension to SQL)
>  - SQL을 확장한 절차적 언어(Procedural Language)
>  - Oracle의 표준 데이터 엑세스 언어, 프로시저 생성자를 SQL과 완벽하게 통합
>  - 유저 프로세스가 PL/SQL 블록을 보내면, 서버 프로세서는 PL/SQL Engine에서 해당 블록을 받고 SQL과 Procedural를 나눠서 SQL은 SQL Statement Executer로 보낸다.
>  - PL/SQL 프로그램의 종류는 크게 Procedure, Function, Trigger 로 나뉘어 진다.
>  - 오라클에서 지원하는 프로그래밍 언어의 특성을 수용하여 SQL에서는 사용할수없는 절차적 프로그래밍 기능을 가지고 있어 SQL의 단점을 보완하였다.

## - dist (distribution)
> - 배포되는 파일이 들어있는 디렉토리
> - 부가코드(이미 존재하는 소스코드를 변환한 코드나 섞일 수 없는 코드처럼)를 저장할 장소 혹은 디렉토리를 나타낸다.

## - 클럭 (@ CPU)
> 클럭 신호는 메트로놈 박자처럼 1초에 몇 번 반복되는 형식으로 측정한다.  
> 클럭 신호가 빠르게 반복될 수록, 박자. 즉 **컴퓨터가 실행될 수 있는 주기**가 빨라진다.
> 그러면 CPU는 `명령어 사이클`을 더 빠르게 반복할 수 있다.  
> -> **클럭 속도 == CPU의 속도 단위**

## - ORM Framework(Object Relational Mapping)
> - 객체 지향 프로그래밍 언어와 관계형 데이터베이스의 호환되지 않는 유형 시스템 간에 데이터를 변환하는 데 사용되는 프로그래밍 기술
> - 비유하면, 객체지향 세계와 RDB 세계를 이어주는 다리!

## - JPA (Java Persistence API)
> JPA는 자바의 ORM기술을 쉽게 구현하도록 도와주는 API이다.
> ex) **1. 엔티티 클래스 정의**
> **데이터베이스 테이블과 매핑될 엔티티 클래스를 정의**한다. 이때, 엔티티 클래스는 @Entity 어노테이션을 이용하여 정의한다. 예를 들어, 다음과 같이 User 엔티티 클래스를 정의할 수 있다.

```
@Entity // 엔티티 클래스임을 선언.
@Table(name = "users") // 해당 엔티티 클래스와 매핑될 데이터베이스 테이블 이름을 지정.
public class User {

  @Id // 엔티티 클래스의 주요 식별자(primary key)임을 선언
  @GeneratedValue(strategy = GenerationType.IDENTITY) // 엔티티의 식별자 값을 자동으로 생성
  private Long id;

  // 해당 엔티티 클래스의 필드가 데이터베이스의 칼럼으로 매핑될 때,
  // 해당 칼럼의 제약 조건을 설정하는 어노테이션입니다. (널허용 = x 등)
  @Column(nullable = false, unique = true) 
  private String username;

  @Column(nullable = false)
  private String password;

  // getters and setters
}
```

출처: [https://ccomccomhan.tistory.com/131](https://ccomccomhan.tistory.com/131) [[꼼꼼한 개발자] 꼼코더:티스토리]

## - binary
> "binary"는 실행 가능한 프로그램 파일 또는 컴퓨터가 직접 실행할 수 있는 형태로 컴파일된 소프트웨어를 의미합니다. 소스 코드가 사람이 읽을 수 있는 형태라면, 바이너리는 컴퓨터가 이해할 수 있는 기계어 형태입니다.
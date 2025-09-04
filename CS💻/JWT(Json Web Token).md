
인터넷 표준 인증 방식
Json 객체에 인증에 필요한 정보들을 담은 후, 비밀키로 서명한 토큰


https://www.jwt.io/
[[HTTP 통신]]

[session 기반 인증, 토큰 기반 인증](https://velog.io/@syi9595/JWTJson-Web-Token%EC%9D%80-%EC%99%9C-%EC%82%AC%EC%9A%A9%EB%90%A0%EA%B9%8C)


## 구조

`header(5).payload(5).signature(5)`

`header`
- alg : Signature에서 사용하는 알고리즘
- typ : 토큰 타입

Base64url 로 인코딩되어있음


`payload`
사용자 정보의 한 조각인 클레임이 들어 있음
- sub : 토큰 제목(subject)
- aud : 토큰 대상자(audience)
- iat : 토큰이 발급된 시각 (issued at)
- exp : 토큰의 만료 시각 (expired)

Base64url 로 인코딩되어있음


`signature`
header, payload를 합친 후 헤더에서 선언한 알고리즘과 key를 이용해 암호화한 값
- key가 없으면 복호화할 수 없다
- header에서 선언한 알고리즘에 따라 key는 개인키가 될 수도 있고 비밀키가 될 수도 있다. 개인키로 서명했다면 공개키로 유효성 검사를 할 수 있고, 비밀키로 서명했다면 비밀키를 가지고 있는 사람만이 암호화 복호화, 유효성 검사를 할 수 있다.




## 분류

- **Access Token**
인증된 사용자가 어느 정도 기간동안 재인증 하지 않아도 되도록(로그인이 유지되도록) 하는 토큰
실질적인 인증정보

- **Refresh Token**
Refresh Token은 Access Token을 다시 발급받기 위한 JWT. 사용은 옵션!
> 로그인을 했을 때 서버에서 `Access Token`, `Refresh Token`을 동시에 보내주는데 둘의 유효기간을 다르게 해서 보낸다. `Refresh Token`을 한 달, `Access Token` 을 하루로 잡았다면  `Access Token`의 기간이 다 되어도 `Refresh Token`의 기간이 남아있기 때문에  사용자는 로그인 없이 다시 `Access Token`을 발급 받을 수 있다. (로그인 유지)





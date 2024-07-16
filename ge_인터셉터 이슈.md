071624

인터셉터 이슈.

GameIntercepter를 타야지 www.으로 넘어가는데..

기존 정책 잡혀있는것 리다이렉트 이슈가 있어서.. 블럭은 나중에

dispatcherInterceptor 에 GameIntercepter를 탈 수 있도록 매핑..?
preSignup에 매핑...?

테스트 안되면 그냥 기존 url쓴다고 하고, 전달도 그렇게 ㄱㄱ!


https://www.mangot5.com/Index/Member/Login?ref=/preSignup/ge/index

src/com/config/spring/dispatcher-interceptor.xml
```
<!-- 각 게임 홈페이지별 URL 전환용 인터셉터 -->
<mvc:interceptor>
    <mvc:mapping path="/game/**" />
    <mvc:mapping path="/*/index"/>
    <mvc:exclude-mapping path="/game/*/charge/**" />
    <mvc:exclude-mapping path="/*/Billing/**" />
    <bean class="com.jc.util.interceptor.GameInterceptor"/>
</mvc:interceptor>
```

이 사이에 
```<mvc:mapping path="/preSignup/*/index"/>``` 이거 추가하는걸루


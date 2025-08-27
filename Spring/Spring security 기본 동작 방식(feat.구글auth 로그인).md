별도의 추가 작업 없이 사용자가 OAuth2(Google 등)를 통해 성공적으로 로그인하면, 
해당 사용자의 인증 정보(`Authentication` 객체, `OAuth2User`를 포함)를 **HTTP 세션에 자동으로 저장**


## Spring Security의 기본 동작 방식

1. **로그인 성공**: 사용자가 Google 로그인을 성공적으로 마칩니다.
2. **`Authentication` 객체 생성**: Spring Security는 로그인한 사용자의 정보(`OAuth2User`)를 담은 `Authentication` 객체를 생성합니다.
3. **`SecurityContext`에 저장**: 이 `Authentication` 객체를 `SecurityContext`에 저장합니다.
4. **세션에 `SecurityContext` 저장**: Spring Security는 이 `SecurityContext`를 **HTTP 세션에 저장**합니다.
    
사용자는 페이지를 새로고침하거나 다른 페이지로 이동해도 로그인 상태가 유지됨
서버는 각 요청마다 세션에서 `SecurityContext`를 꺼내 현재 사용자가 누구인지 파악함





## `@AuthenticationPrincipal`의 작동 원리

`@AuthenticationPrincipal OAuth2User user` 어노테이션은 세션에 저장된 정보를 가져와 사용하는 대표적인 예

`@AuthenticationPrincipal`은 현재 세션의 `SecurityContext`에 저장된 `Authentication` 객체에서 Principal(`OAuth2User`)을 직접 꺼내어 컨트롤러 메소드의 파라미터로 주입함
**세션에 정보가 저장되어 있지 않다면 `@AuthenticationPrincipal`은 `null`을 반환**

---

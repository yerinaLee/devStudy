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

질문자님의 코드에서 사용된 `@AuthenticationPrincipal OAuth2User user` 어노테이션이 바로 이 세션에 저장된 정보를 가져와 사용하는 대표적인 예입니다.

`@AuthenticationPrincipal`은 현재 세션의 `SecurityContext`에 저장된 `Authentication` 객체에서 Principal(`OAuth2User`)을 직접 꺼내어 컨트롤러 메소드의 파라미터로 주입해주는 편리한 기능입니다. 즉, **세션에 정보가 저장되어 있지 않다면 `@AuthenticationPrincipal`은 `null`을 반환**하게 됩니다.

---

### ## 세션 정보 직접 접근하기 (참고)

만약 컨트롤러가 아닌 다른 서비스 레이어 등에서 현재 로그인한 사용자 정보가 필요하다면, 다음과 같이 `SecurityContextHolder`를 통해 세션에 저장된 정보에 접근할 수 있습니다.

Java

```
import org.springframework.security.core.Authentication;
import org.springframework.security.core.context.SecurityContextHolder;
import org.springframework.security.oauth2.core.user.OAuth2User;
import org.springframework.stereotype.Service;

@Service
public class MyService {

    public void doSomethingWithUser() {
        // SecurityContextHolder에서 현재 Authentication 정보를 가져옴
        Authentication authentication = SecurityContextHolder.getContext().getAuthentication();

        if (authentication != null && authentication.getPrincipal() instanceof OAuth2User) {
            OAuth2User oauth2User = (OAuth2User) authentication.getPrincipal();

            // 이제 oauth2User 객체로 사용자 정보에 접근 가능
            String name = oauth2User.getAttribute("name");
            String email = oauth2User.getAttribute("email");
            System.out.println("Current User Name: " + name);
            System.out.println("Current User Email: " + email);
        } else {
            // 로그인하지 않은 사용자 또는 다른 타입의 Principal인 경우
            System.out.println("User is not authenticated or not an OAuth2 user.");
        }
    }
}
```

### **결론**

> **별도의 설정을 하지 않았다면, Spring Security가 기본적으로 Google Auth 사용자 정보를 세션에 저장하고 관리해줍니다.** 질문자님의 코드는 이미 그 기능을 활용하고 있는 것입니다.
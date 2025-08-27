```
public String logout(HttpServletRequest request, HttpServletResponse response, @AuthenticationPrincipal OAuth2User user){  
    // user 정보가 없을 경우 리턴  
    Authentication auth = SecurityContextHolder.getContext().getAuthentication();  
    System.out.println("auth : " + auth);  
    System.out.println("user : " + user);
```



auth : OAuth2AuthenticationToken [Principal=Granted Authorities: [[OAUTH2_USER, SCOPE_https://www.googleapis.com/auth/userinfo.email, SCOPE_https://www.googleapis.com/auth/userinfo.profile, SCOPE_openid]], User Attributes: [{sub=106989961992096333369, name=ri ye, given_name=ri, family_name=ye, picture=https://lh3.googleusercontent.com/a/ACg8ocJoSjto-WiLHnua0Da7spjssNCSOCm-zPg-LflKMKuHVr_Y-w=s96-c, email=yeri042924@gmail.com, email_verified=true}], Credentials=[PROTECTED], Authenticated=true, Details=WebAuthenticationDetails [RemoteIpAddress=0:0:0:0:0:0:0:1, SessionId=F8805F4ECFBC3B2BB4FA8FC2F1CAAE2B], Granted Authorities=[OAUTH2_USER, SCOPE_https://www.googleapis.com/auth/userinfo.email, SCOPE_https://www.googleapis.com/auth/userinfo.profile, SCOPE_openid]]


user : Name: [106989961992096333369], Granted Authorities: [[OAUTH2_USER, SCOPE_https://www.googleapis.com/auth/userinfo.email, SCOPE_https://www.googleapis.com/auth/userinfo.profile, SCOPE_openid]], User Attributes: [{sub=106989961992096333369, name=ri ye, given_name=ri, family_name=ye, picture=https://lh3.googleusercontent.com/a/ACg8ocJoSjto-WiLHnua0Da7spjssNCSOCm-zPg-LflKMKuHVr_Y-w=s96-c, email=yeri042924@gmail.com, email_verified=true}]

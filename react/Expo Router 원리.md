Expo Router : 파일 기반 라우팅
`app/` 폴더 하위 파일 위치가 곧 화면 주소임


## 핵심 규칙

1 . 괄호 폴더 : 그룹핑
화면을 묶어 정리만 하고, 주소에는 보이지 않음

ex) `app/(auth)/login.js` -> 실제 주소는 `/auth/login` 이 아니라 `/login`


2 . 대괄호 파일 : 동적 경로
주소의 일부가 변수가 됨

ex) `app/(views)/community/detail/[id].js` 에서
`/community/detail/123` 주소를 받아내고, 컴포넌트 안에서 `useLocalSearchParams()` 로 `{id : '123'}` 을 꺼내서 씀



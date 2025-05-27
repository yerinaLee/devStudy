1. **클라이언트 요청**: 다수의 클라이언트가 동시에 SQL 요청
2. **라이브러리 캐시 조회**: 실행할 SQL이 라이브러리 캐시에 존재하는지 확인
3. **parent cursor 조회**  
    - 기존 parent cursor를 재사용할 수 있는 경우: child cursor 조회
    - 적합한 parent cursor가 없는 경우: 하드 파싱 수행
4. **child cursor 재사용/생성**  
    - 바인딩 값이 일치하면 기존 child cursor를 재사용 → 소프트 파싱 수행
    - 적합한 child cursor가 없으면 새로운 child cursor 생성 → **부분적 하드 파싱 발생**
5. **실행 후 결과 반환**
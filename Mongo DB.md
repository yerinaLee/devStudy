## MongoDB 모델링 방법

[https://blog.voidmainvoid.net/241](https://blog.voidmainvoid.net/241)  ** 작성 잘되있음
[https://velog.io/@swhan9404/mongoDB-개념잡기](https://velog.io/@swhan9404/mongoDB-%EA%B0%9C%EB%85%90%EC%9E%A1%EA%B8%B0)

[https://jhleeeme.github.io/mongodb-collection-find/](https://jhleeeme.github.io/mongodb-collection-find/)  ** 문법

[https://lts0606.tistory.com/568](https://lts0606.tistory.com/568)  ** 조회 문법

mongoTemplate 사용법
[https://www.baeldung.com/queries-in-spring-data-mongodb](https://www.baeldung.com/queries-in-spring-data-mongodb)

#### 특징
- 테이블과 같은 schema가 없으며, **JSON형태의 문서 지향적 NoSQL 데이터베이스**
- **database > collections > documents 구조**로 document는 key-value형태의 BSON(Binary JSON)으로 되어있다.
#### 장점
- Read & Write 성능이 뛰어나다. 캐싱이나 많은 트래픽을 감당할 때 써도 좋다.
-  **MongoDB는 다른 nosql에 비해 Index가 강점**이다. 관계형 데이터베이스 수준의 인덱스 기능을 제공. 해결을 위해 해쉬 사용 가능

#### 단점
- JOIN이 없다. join이 필요없도록 데이터 구조화 필요
- memory mapped file으로 파일 엔진 DB이다. 메모리 관리를 OS에게 위임한다. 메모리에 의존적, 메모리 크기가 성능을 좌우한다.

---

![](https://velog.velcdn.com/images%2Fswhan9404%2Fpost%2Ffb7b9b0d-7b7d-4ab6-ab4a-cd19c4602280%2Fimage.png)

![](https://velog.velcdn.com/images%2Fswhan9404%2Fpost%2Ff78649a4-b216-4814-91d6-398deb309dcd%2Fimage.png)



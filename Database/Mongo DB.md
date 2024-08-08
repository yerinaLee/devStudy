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
- 단일 문서의 크기는 16MB 제한됨
#### 장점
- Read & Write 성능이 뛰어나다. 캐싱이나 많은 트래픽을 감당할 때 써도 좋다.
-  **MongoDB는 다른 nosql에 비해 Index가 강점**이다. 관계형 데이터베이스 수준의 인덱스 기능을 제공. 해결을 위해 해쉬 사용 가능

#### 단점
- JOIN이 없다. join이 필요없도록 데이터 구조화 필요
- memory mapped file으로 파일 엔진 DB이다. 메모리 관리를 OS에게 위임한다. 메모리에 의존적, 메모리 크기가 성능을 좌우한다.

### 용어정리
- 클러스터
    인스턴스들의 모임, 데이터를 저장하는 서버 그룹

- 레플리카 세트
    단일 클러스터에서 각각의 인스턴스는 동일한 복제본을 가지고 있으며 이모음을 레플리카 세트라고 한다. 데이터의 사본을 저장하는 인스턴스의 모음. 동일한 데이터를 저장하는 소수의 연결된 머신들은 머신 중 하나에 문제가 발생하더라도 데이터가 그대로 유지되도록 합니다.

- 인스턴스
    로컬 또는 클라우드에서 특정 소프트웨어를 실행하는 단일 머신, MongoDB에서는 데이터베이스입니다.



---

![](https://velog.velcdn.com/images%2Fswhan9404%2Fpost%2Ffb7b9b0d-7b7d-4ab6-ab4a-cd19c4602280%2Fimage.png)

![](https://velog.velcdn.com/images%2Fswhan9404%2Fpost%2Ff78649a4-b216-4814-91d6-398deb309dcd%2Fimage.png)



### Document

```javascript
{
    "_id": ObjectId("5099803df3f4948bd2f98391"),
    "username": "ljh",
    "name": { first: "J.H.", last: "Lee" }
}
```


### import, export 명령어

- **JSON** 형식
    - **mongoimport** : 데이터를 가져오는 명령어
    - **mongoexport** : 데이터를 내보내기 위한 명령어
- **BSON** 형식
    - **mongorestore** : 데이터를 가져오는 명령어
    - **mongodump** : 데이터를 내보내기 위한 명령어



### 사용 팁
- 1차 메모리 사용(데이터,인덱스) 만약 없다면 2차로 물리 데이터를 사용하는데 이 과정에서 성능 저하가 발생함  
- 이에 key 생성시 검색할 때 **자주 사용되는 필드를 concat한 후 hash1 생성하여 id 필드를 사용**하는걸 권장 함

- 자주 액세스되는 데이터를 **Hot Data**라고 하는데, 이 데이터들이 집중되서 메모리에 올라가도록 Key 설계를 하는 것이 핵심  
- 키설계 방법 : 항상 검색할 때 사용하는 필드를 concat한 값에 대해 해시값을 생성한 후 **id 필드값으로 사용한다.**

### 최적화 전략  
- 전체 데이터를 scan하는 등의 작업을 하게 되면, 무조건 페이지 폴트가 발생하기에 table scan이 필요한 시나리오는 별도의 index table(summary table)을 만들어서 사용하는 등의 전략이 필요

### 사용법  
    1:N

1. **인덱스가 클 경우**
해결책 :
- 항상 검색할 때 사용하는 필드를 concat한 값에 대해 해시값을 생성한 후 _id 필드값으로 사용한다.
- SHA-1 알고리즘의 경우 경우의 수가 2^160 이므로 충돌회피가 가능하다.

Humongous DB ▪ Document DB : BSON(Binary JSON) ▪ Auto Sharding ▪ Replica Set ▪ Index : Geospatial(위치정보 처리 index), Hashed, Unique, Spars, Compound - Embedded Document, Array 필드도 인덱싱..

### MongoDB document 패턴  
- 1:1 패턴
```
{  
"emp_id" : 1001,  
"emp_name" : "홍길동",  
"reg_number" : "111111-1111111"  
}
```

Aggregation --> Embedded Document


### embedded , link 결정 체크분기
![[Pasted image 20240805135346.png]]

방법 1) embedded : 자식 객체가 단독으로 사용되지 않고 부모객체 내에서만 사용될 때 사용.

- 예) 주문 정보와 주문 세부 항목 정보
- 한번의 Read로 필요한 정보 모두를 읽어옴 → 읽기 성능 향상
- Strong Association


방법 2) linked : 자식객체가 부모객체와는 별개로 단독으로 사용될 때 적용

■ Linked Document는 기존 관계형 데이터베이스 처럼 비정규화하지 않고, 두개의 테이블로 분리시키는 방법이다. 제약조건이 없다는 점을 제외하면 관계형 데이터베이스와 동일하다고 볼 수 있다.

- 예) 상품 분류 정보와 상품 정보

-상품분류별 상품 정보들을 조회하려면 여러번 Read를 해야 함. → 읽기 성능 저하
-데이터 일관성이 상대적으로 중요할 때 사용
-Weak Association



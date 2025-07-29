 
# ✅ DDD란? (Domain-Driven Design)

### ▶️ **정의**

DDD는 복잡한 도메인(=업무 영역)을 **"모델 중심"**으로 설계하고, **비즈니스 로직을 도메인에 집중**시키는 설계 철학이에요.

---

## 🧠 핵심 개념 요약

|용어|의미|
|---|---|
|**Entity**|고유 ID를 가진 객체 (예: `User`, `Order`)|
|**Value Object**|의미는 있지만 ID 없는 값 (예: `Money`, `Address`)|
|**Aggregate**|여러 객체를 포함한 비즈니스 루트 단위|
|**Repository**|Entity를 저장/조회하는 책임|
|**Service**|도메인 규칙을 조합해 동작을 수행|
|**Bounded Context**|특정 도메인 의미가 일관되게 유지되는 경계 영역|

---

### 📘 DDD 예시

**도메인 시나리오**: "고객이 도서관에서 책을 빌린다. 기한을 넘기면 연체료가 발생한다."

#### DDD 설계 요소:

```groovy
// 도메인
class Book {
    String title
    LocalDate dueDate

    boolean isOverdue() {
        return dueDate.isBefore(LocalDate.now())
    }
}

// 서비스
class BookService {
    BigDecimal calculateLateFee(Book book) {
        if (!book.isOverdue()) return 0
        def days = ChronoUnit.DAYS.between(book.dueDate, LocalDate.now())
        return days * 1000
    }
}
```

#### TDD로 검증:

- BookServiceSpec에서 "연체일 계산", "0원일 경우", "10일 초과 시" 등 시나리오로 테스트  
    → TDD와 DDD는 **서로 보완적**이에요
    

---

# 🔄 TDD와 DDD는 어떻게 연결될까?

|TDD 관점|DDD 관점|
|---|---|
|먼저 테스트를 작성해 "어떻게 동작해야 할지" 정의|도메인을 중심으로 비즈니스 개념과 책임을 설계|
|테스트가 모델과 비즈니스 로직에 집중됨|설계된 도메인을 테스트로 검증함|
|테스트 단위는 도메인 로직, 서비스 단위|도메인이 "언제, 어떤 책임을 수행해야 하는지" 테스트로 명확히 됨|

> 즉, DDD는 “무엇을 테스트해야 할지” 방향을 제시하고, TDD는 “어떻게 검증할지” 도구를 제공해요.

---

## 📌 정리

|항목|설명|
|---|---|
|TDD|테스트 먼저 → 코드 작성 → 리팩터링. **실행 중심 개발 방식**|
|DDD|도메인 모델 중심으로 복잡한 비즈니스 로직을 **설계하는 사고방식**|
|Grails|TDD와 DDD에 모두 친화적: Spock 기반 테스트, 도메인 중심 설계 지원|
|결론|TDD는 "행동 중심", DDD는 "모델 중심". 함께 쓰면 최고의 효과 💡|

---

필요하다면 실제 Grails 프로젝트에서 **TDD-Driven으로 CRUD 구현하는 흐름**,  
또는 **DDD 구조 예제 프로젝트 구조**도 같이 보여드릴 수 있어요. 원할까요?

# ✅ 1. TDD란? (Test-Driven Development)

### ▶️ **정의**

**“테스트를 먼저 작성하고, 나중에 코드를 짜는 개발 방식”**

### ▶️ **핵심 흐름 (Red → Green → Refactor)**

1. **Red**: 실패하는 테스트를 먼저 작성한다   
2. **Green**: 테스트를 통과시키기 위한 최소한의 코드를 작성
3. **Refactor**: 코드를 리팩터링하며 구조를 개선


1단계 실패하는 테스트 작성 →  
2단계 실제 코드 작성 (테스트 통과) →  
3단계 코드 정리 (리팩터링)

기능을 구현하기 전에 "**이 코드가 어떻게 동작해야 하는지**"부터 명확히 정의하는 것


## 🧪 Grails에서 TDD 시작하는 방법

Grails는 **Spock 테스트 프레임워크**를 기본으로 사용, 도메인, 서비스, 컨트롤러 단위의 테스트 템플릿을 자동 생성함


### 📦 예제 프로젝트 구조 (기본)

```
grails-app/
├── controllers/
├── domain/
├── services/
└── ...
src/test/groovy/
├── myapp/
│   ├── BookSpec.groovy      ← 도메인 테스트
│   ├── BookServiceSpec.groovy
│   └── BookControllerSpec.groovy
```


소스코드 위치 : `test/unit/com/common/auth/AuthServiceSpec.groovy`
 
```groovy
@TestFor(CttLogController)  // 테스트 대상 지정
class CttLogControllerSpec extends Specification {
    
    def setup() {}         // 각 테스트 전에 실행됨
    def cleanup() {}       // 각 테스트 후에 실행됨

    void "test something"() {
        // 여기에 실제 테스트 시나리오 작성!
    }
}
```





## ✅ 예시1. : Book 도메인에 대한 TDD 흐름

#### 1) 실패하는 테스트 먼저 작성 (Red)

```groovy
// BookServiceSpec.groovy
void "should calculate late fee for overdue book"() {
    given:
    def book = new Book(title: "Clean Code", dueDate: LocalDate.now().minusDays(5))

    when:
    def fee = bookService.calculateLateFee(book)

    then:
    fee == 5000  // 하루 1000원 * 5일 = 5000원
}
```

#### 2) 실제 로직 작성 (Green)

```groovy
// BookService.groovy
BigDecimal calculateLateFee(Book book) {
    def daysOverdue = ChronoUnit.DAYS.between(book.dueDate, LocalDate.now())
    return daysOverdue > 0 ? daysOverdue * 1000 : 0
}
```

#### 3) 리팩터링 (Refactor)

- magic number 제거
- 메시지 중심 인터페이스로 개선 등

---





## ✅ 예시 2 : 연체료 계산하기

### 🎯 목표

- 연체된 책이 있으면 하루당 1,000원씩 연체료가 붙는다
- 예: 5일 연체 → 5 * 1000 = 5000원


## 📌 1단계: 실패하는 테스트 먼저 작성 (Red 단계)

먼저 `BookServiceSpec.groovy`에 아래처럼 테스트 코드를 작성해요.  
(없으면 `grails create-service Book`으로 BookService 만들고, `grails create-unit-test BookService` 해주세요)

```groovy
import spock.lang.Specification
import java.time.LocalDate
import java.time.temporal.ChronoUnit

class BookServiceSpec extends Specification {

    def bookService = new BookService() // 테스트 대상 인스턴스

    void "should calculate late fee for overdue book"() {
        given: "A book that is 5 days overdue"
        def book = new Book(title: "Clean Code", dueDate: LocalDate.now().minusDays(5))

        when: "We calculate the late fee"
        def fee = bookService.calculateLateFee(book)

        then: "The fee should be 5000"
        fee == 5000
    }
}
```



## 📌 2단계: 실제 기능을 구현해서 테스트 통과시키기 (Green 단계)

`BookService.groovy` 파일을 만들고 (또는 이미 있다면 수정):

```groovy
import java.time.LocalDate
import java.time.temporal.ChronoUnit

class BookService {

    BigDecimal calculateLateFee(Book book) {
        def daysOverdue = ChronoUnit.DAYS.between(book.dueDate, LocalDate.now())
        return daysOverdue > 0 ? daysOverdue * 1000 : 0
    }
}
```

그리고 `Book.groovy`라는 도메인 클래스도 필요해요:

```groovy
class Book {
    String title
    LocalDate dueDate
}
```



## 📌 3단계: 리팩터링 (코드 정리 단계)

- 하드코딩된 **1000** 숫자를 상수로 빼기
- `isOverdue()` 같은 메서드로 의미 부여

```groovy
class Book {
    String title
    LocalDate dueDate

    boolean isOverdue() {
        return dueDate.isBefore(LocalDate.now())
    }

    long overdueDays() {
        return isOverdue() ? ChronoUnit.DAYS.between(dueDate, LocalDate.now()) : 0
    }
}
```

```groovy
class BookService {

    static final BigDecimal LATE_FEE_PER_DAY = 1000

    BigDecimal calculateLateFee(Book book) {
        return book.overdueDays() * LATE_FEE_PER_DAY
    }
}
```




# ✅ 테스트 실행 방법

터미널에서 프로젝트 루트로 가서:

```bash
grails test-app
```

성공하면 ✅ 초록색 통과 표시  
실패하면 ❌ 빨간색 에러와 함께 실패 원인 보여줌





# 🔁 요약 정리

|단계|설명|우리가 한 것|
|---|---|---|
|Red|실패하는 테스트 작성|`BookServiceSpec.groovy`에서 예상 시나리오|
|Green|기능 최소 구현 → 테스트 통과|`calculateLateFee()` 메서드 작성|
|Refactor|하드코딩 제거, 의미 있는 코드로 정리|상수, 메서드 분리 등|


## 🛠 Grails에서 테스트 작성 팁

| 대상       | 명령어                                       |
| -------- | ----------------------------------------- |
| 도메인 테스트  | `grails create-domain-class Book` → 자동 생성 |
| 서비스 테스트  | `grails create-service BookService`       |
| 컨트롤러 테스트 | `grails create-controller Book`           |
| 테스트 실행   | `./grailsw test-app` 또는 `grails test-app` |




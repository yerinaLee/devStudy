
# ✅ 1. TDD란? (Test-Driven Development)

### ▶️ **정의**

TDD는 **“테스트를 먼저 작성하고, 나중에 코드를 짜는 개발 방식”**이에요.

### ▶️ **핵심 흐름 (Red → Green → Refactor)**

1. **Red**: 실패하는 테스트를 먼저 작성한다   
2. **Green**: 테스트를 통과시키기 위한 최소한의 코드를 작성
3. **Refactor**: 코드를 리팩터링하며 구조를 개선

> 즉, 기능을 구현하기 전에 "이 코드가 어떻게 동작해야 하는지"부터 명확히 정의하는 거예요.

---

## 🧪 Grails에서 TDD 시작하는 방법

Grails는 Spock 테스트 프레임워크를 기본으로 사용하며, **도메인, 서비스, 컨트롤러 단위의 테스트 템플릿**을 자동 생성해줘요.

---

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


 위치 : `test/unit/com/common/auth/AuthServiceSpec.groovy`
 
```
package com.common.auth  
  
import grails.test.mixin.TestFor  
import spock.lang.Specification  
  
/**  
 * See the API for {@link grails.test.mixin.services.ServiceUnitTestMixin} for usage instructions  
 */@TestFor(AuthService)  
class AuthServiceSpec extends Specification {  
  
    def setup() {  
    }  
  
    def cleanup() {  
    }  
  
    void "test something"() {  
    }  
}
```





---

### ✅ 예시: Book 도메인에 대한 TDD 흐름

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

## 🛠 Grails에서 테스트 작성 팁

|대상|명령어|
|---|---|
|도메인 테스트|`grails create-domain-class Book` → 자동 생성|
|서비스 테스트|`grails create-service BookService`|
|컨트롤러 테스트|`grails create-controller Book`|
|테스트 실행|`./grailsw test-app` 또는 `grails test-app`|


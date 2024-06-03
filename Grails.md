- API url  매핑 위치 : UrlMappings.groovy

#### 스캐폴딩
도메인 클래스를 기반으로 기본적인 CRUD(Create, Read, Update, Delete) 기능을 자동으로 생성

---

### - URL 매핑
Grails에서 API 매핑은 주로 URL 매핑을 통해 이루어짐.

#### 원리
1. **설정 파일**: `UrlMappings.groovy` 파일에서 URL 매핑을 관리
	`grails-app/conf` 디렉토리에 위치. URL 패턴과 이에 대응하는 컨트롤러 및 액션을 정의함.
    
2. **매핑 정의**: URL 매핑은 선언적으로 정의됨. 각 매핑은 HTTP 메소드, URL 패턴, 컨트롤러, 액션 등을 지정할 수 있습니다. 예를 들어, 특정 URL 패턴에 대해 GET 요청을 처리하는 컨트롤러의 액션을 지정할 수 있습니다.
```groovy
class UrlMappings {
	static mappings = {
		"/book/$id"(controller: "book", action: "show") {
			constraints {
				// 요청 파라미터에 대한 제약조건 추가 가능
				id(matches: /\d+/) // 숫자만 허용
			}
		}
		"/api/book"(controller: "book", action: [GET: "list", POST: "save"]) 
		// HTTP 메소드에 따른 액션 지정
	}
}
```

3. **동적 URL 매핑**: `$` 기호를 사용하여 URL 내에 변수를 포함가능. ex) `/book/$id`와 같은 매핑은 다양한 `id` 값에 대해 동일한 컨트롤러 액션을 사용할 수 있음

4. **네임스페이스와 RESTful API**: Grails는 API 개발을 위한 RESTful 컨벤션을 지원합니다. `@Resource` 어노테이션을 사용하여 도메인 클래스를 RESTful 리소스로 쉽게 노출할 수 있습니다. 또한, 네임스페이스를 사용하여 API 버전을 관리하는 것도 가능합니다.

5. **인터셉터**: 매핑된 액션을 실행하기 전후로 추가적인 로직을 실행할 수 있게 하는 인터셉터도 지원됩니다. 이를 통해 권한 검사, 로깅 등의 기능을 쉽게 추가할 수 있습니다.

Grails의 URL 매핑 원리는 개발자가 웹 애플리케이션의 구조를 빠르게 이해하고, 유연하게 URL을 관리할 수 있도록 도와줍니다. 또한, RESTful API 개발을 위한 강력한 지원을 제공하여, 현대적인 웹 서비스 개발에 적합합니다.

---

### 스캐폴딩(Scaffolding)

스캐폴딩은 Grails에서 매우 강력한 기능으로, 도메인 클래스를 기반으로 기본적인 CRUD(Create, Read, Update, Delete) 기능을 자동으로 생성해줍니다. 이 기능을 통해 개발자는 최소한의 코드 작성으로도 애플리케이션을 빠르게 프로토타이핑할 수 있습니다.

#### 스캐폴딩의 종류:

1. **동적 스캐폴딩**: 개발 중에 빠르게 CRUD 기능을 확인하고 싶을 때 사용합니다. 도메인 클래스의 컨트롤러에 `static scaffold = true`를 설정하면 됩니다.
```groovy
class BookController {
	static scaffold = Book
}
```
    
2. **정적 스캐폴딩**: 실제 코드 파일을 생성하여 커스터마이징이 필요할 때 사용합니다. Grails CLI 명령어를 통해 컨트롤러 및 뷰 파일을 생성할 수 있습니다.
    ```sh
grails generate-all Book
    ```

### URL 매핑과 스캐폴딩의 연관성

#### 1. 기본 URL 매핑 제공:

스캐폴딩을 사용하면 Grails는 자동으로 기본 URL 매핑을 설정합니다. 예를 들어, `Book` 도메인 클래스에 대해 스캐폴딩을 설정하면, Grails는 `/book` 경로에 대한 기본 CRUD 액션을 자동으로 매핑합니다.

- `/book/index` - 리스트 보기
- `/book/show/1` - 특정 항목 보기
- `/book/create` - 새 항목 생성 폼
- `/book/save` - 새 항목 저장
- `/book/edit/1` - 특정 항목 편집 폼
- `/book/update/1` - 특정 항목 업데이트
- `/book/delete/1` - 특정 항목 삭제

#### 2. 커스터마이징 가능:

스캐폴딩으로 생성된 기본 매핑 외에도, `UrlMappings.groovy`를 통해 추가적인 URL 매핑을 정의하거나 기존 매핑을 커스터마이징할 수 있습니다. 이를 통해 더 복잡한 요구사항을 충족할 수 있습니다.

#### 3. RESTful API 지원:

스캐폴딩은 RESTful API 개발에도 유용합니다. Grails는 기본적으로 RESTful 컨벤션을 따르며, 스캐폴딩을 통해 생성된 컨트롤러는 RESTful 엔드포인트를 제공합니다. 이를 URL 매핑과 결합하면, 보다 유연하고 강력한 API를 설계할 수 있습니다.

### 결론

Grails의 스캐폴딩 기능은 URL 매핑과 긴밀하게 연관되어 있습니다. 스캐폴딩을 통해 생성된 기본 CRUD 기능은 자동으로 URL 매핑을 설정하며, 이를 통해 개발자는 빠르게 애플리케이션을 시작할 수 있습니다. 또한, 필요에 따라 `UrlMappings.groovy` 파일을 통해 매핑을 커스터마이징하고 확장할 수 있습니다. 이 두 기능의 조합은 Grails의 생산성을 높이는 중요한 요소입니다.


------


URL 매핑(URL Mapping)은 웹 애플리케이션에서 특정 URL 경로를 특정 컨트롤러와 액션에 연결하는 과정을 의미합니다. 이를 통해 사용자가 웹 브라우저에서 입력한 URL이 애플리케이션 내의 어떤 로직을 실행할지 결정할 수 있습니다.

### URL 매핑의 역할

1. **경로 지정**: 사용자가 입력한 URL을 애플리케이션 내부의 특정 컨트롤러와 액션에 매핑합니다.
2. **경로 간소화**: 복잡한 경로나 긴 URL을 간단하게 만들어 사용자 경험을 개선합니다.
3. **RESTful API 설계**: RESTful API를 설계할 때, URL 매핑을 통해 각 HTTP 메소드(GET, POST, PUT, DELETE 등)에 맞는 엔드포인트를 정의합니다.

### Grails에서의 URL 매핑

Grails에서는 URL 매핑을 `UrlMappings.groovy` 파일을 통해 설정합니다. 이 파일은 `grails-app/conf` 디렉토리에 위치하며, 다양한 URL 패턴을 컨트롤러와 액션에 매핑할 수 있습니다.

#### 예제: `UrlMappings.groovy`

```groovy
class UrlMappings {
    static mappings = {
        // 기본 경로 매핑
        "/$controller/$action?/$id?(.$format)?" {
            constraints {
                // 제약 조건 추가 가능
            }
        }

        // 특정 경로 매핑
        "/book/$id"(controller: "book", action: "show") {
            constraints {
                id(matches: /\d+/) // 숫자만 허용
            }
        }

        // RESTful API 매핑
        "/api/book"(controller: "book", action: [GET: "list", POST: "save"])
        "/api/book/$id"(controller: "book", action: [GET: "show", PUT: "update", 
        DELETE: "delete"])

        // 기본 페이지 경로 매핑
        "/"(controller: "home", action: "index")
        "500"(view: '/error')
        "404"(view: '/notFound')
    }
}
```

### 주요 요소

1. **패턴**: URL 패턴을 정의합니다. 예를 들어, `/book/$id`는 `/book/1`, `/book/2` 등의 URL을 매핑합니다.
2. **컨트롤러**: URL이 매핑될 컨트롤러를 지정합니다.
3. **액션**: 컨트롤러 내에서 실행될 액션(메소드)을 지정합니다.
4. **제약 조건**: URL 패턴에 대한 제약 조건을 설정할 수 있습니다. 예를 들어, `id`는 숫자만 허용하도록 할 수 있습니다.
5. **HTTP 메소드**: 특정 HTTP 메소드(GET, POST, PUT, DELETE 등)에 따라 다른 액션을 매핑할 수 있습니다.

### URL 매핑의 장점

- **유연성**: 다양한 URL 패턴을 정의하고, 이를 통해 애플리케이션의 구조를 유연하게 설계할 수 있습니다.
- **가독성**: 간단하고 직관적인 URL을 사용해 사용자 경험을 향상시킵니다.
- **유지보수성**: URL 매핑을 통해 경로를 중앙에서 관리할 수 있어 유지보수가 용이합니다.

결론적으로, URL 매핑은 웹 애플리케이션에서 사용자 요청을 적절한 로직으로 연결하는 중요한 기능이며, Grails는 이를 효율적으로 관리할 수 있는 도구를 제공합니다.

---

### def
Grails에서 `def` 키워드를 사용하여 메소드와 변수를 선언할 수 있다.

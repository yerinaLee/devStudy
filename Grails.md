- API url  매핑 위치 : UrlMappings.groovy

#### 스캐폴딩
도메인 클래스를 기반으로 기본적인 CRUD(Create, Read, Update, Delete) 기능을 자동으로 생성

---

### - URL 매핑
Grails에서 API 매핑은 주로 URL 매핑을 통해 이루어짐.

#### 원리
1. **설정 파일**: `UrlMappings.groovy` 파일에서 URL 매핑을 관리
	`grails-app/conf` 디렉토리에 위치. URL 패턴과 이에 대응하는 컨트롤러 및 액션을 정의함.
    
2. **매핑 정의**: URL 매핑은 선언적으로 정의됨. 각 매핑은 HTTP 메소드, URL 패턴, 컨트롤러, 액션 등을 지정할 수 있음.
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

3. **동적 URL 매핑**: `$` 기호를 사용하여 URL 내에 변수를 포함가능
	ex) `/book/$id`와 같은 매핑은 다양한 `id` 값에 대해 동일한 컨트롤러 액션을 사용

4. **RESTful API**: `@Resource` 어노테이션으로 도메인 클래스를 RESTful 리소스로 노출

5. **인터셉터** 지원


---

### 스캐폴딩(Scaffolding)

도메인 클래스를 기반으로 기본적인 CRUD(Create, Read, Update, Delete) 기능을 자동으로 생성

#### 종류

1. **동적 스캐폴딩**: 개발 중에 빠르게 CRUD 기능을 확인하고 싶을 때 사용
	도메인 클래스의 컨트롤러에 `static scaffold = true` 작성
```groovy
class BookController {
	static scaffold = Book // Book : 도메인 클래스
}
```

2. **정적 스캐폴딩**: 실제 코드 파일을 생성하여 커스터마이징 필요시 사용. Grails CLI 명령어를 통해 컨트롤러 및 뷰 파일 생성
    ```sh
grails generate-all Book
    ```

---

### URL 매핑과 스캐폴딩의 연관성

#### 1. 기본 URL 매핑 제공:

스캐폴딩을 사용시 자동으로 기본 URL 매핑을 설정
ex) `Book` 도메인 클래스에 대해 스캐폴딩을 설정하면, Grails는 `/book` 경로에 대한 기본 CRUD 액션을 자동으로 매핑함

- `/book/index` - 리스트 보기
- `/book/show/1` - 특정 항목 보기
- `/book/create` - 새 항목 생성 폼
- `/book/save` - 새 항목 저장
- `/book/edit/1` - 특정 항목 편집 폼
- `/book/update/1` - 특정 항목 업데이트
- `/book/delete/1` - 특정 항목 삭제

#### 2. 커스터마이징 가능:

기본 매핑 외에도, `UrlMappings.groovy`를 통해 추가적인 URL 매핑을 정의 / 기존 매핑을 커스터마이징 가능

#### 3. RESTful API 지원:

Grails는 기본적으로 RESTful 컨벤션을 따르며, 스캐폴딩을 통해 생성된 컨트롤러는 RESTful 엔드포인트를 제공. 



------

### URL 매핑

: 웹 애플리케이션에서 특정 URL 경로를 특정 컨트롤러와 액션에 연결하는 과정

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


---

### def
Grails에서 `def` 키워드를 사용하여 메소드와 변수를 선언할 수 있다.

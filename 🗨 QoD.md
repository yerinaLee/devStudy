## Q. grails에서 def 는 class와 method 둘 다를 의미하는거야?

`def` 키워드는 Groovy 언어에서 사용되며, Grails는 Groovy를 기반으로 하고 있기 때문에 `def`를 자주 사용합니다. `def`는 타입을 명시하지 않고 변수를 선언하거나 메서드를 정의할 때 사용됩니다. `def` 키워드는 아래와 같은 다양한 상황에서 사용할 수 있습니다.

1. **변수 선언**:
    ```groovy
    def myVariable = "Hello, World!"
    ```

2. **메서드 정의**:
    ```groovy
    def myMethod() {
        println "This is a method"
    }
    ```

3. **클래스 정의**에는 `def`를 사용하지 않습니다. 클래스 정의는 다음과 같이 합니다:
    ```groovy
    class MyClass {
        def myField
        def myMethod() {
            println "This is a method in MyClass"
        }
    }
    ```

따라서, `def`는 주로 변수와 메서드의 타입을 명시하지 않을 때 사용되며, 클래스 정의에는 사용되지 않습니다.

요약하자면, `def`는 변수 선언과 메서드 정의에 사용되며, 클래스 정의에는 사용되지 않습니다.


---

## Q. 쿠키/세션/캐시의 차이점은?

쿠키와 세션의 차이점은 크게 **상태 정보의 저장 위치**이다. 
쿠키는 '클라이언트(= 로컬 = 사용자브라우저)'에 저장하고, 세션은 '서버' 에 저장

캐시 (Cache) : 
리소스 파일들의 임시 저장소. 같은 웹 페이지에 접속할 때 사용자의 PC에서 로드하므로 서버를 거치지 않아도 된다.
이전에 사용되었던 데이터는 다시 사용될 가능성이 높다 -> 그래서 다시 사용될 확률이 있는 데이터들을 빠르게 접근 가능한 저장소에 저장한다.

=> 페이지 로딩 속도를 개선함 
이미지, 비디오 오디오, CSS/JS 등...

#### [정리넘나잘되어잇음!](https://hongong.hanbit.co.kr/%EC%99%84%EB%B2%BD-%EC%A0%95%EB%A6%AC-%EC%BF%A0%ED%82%A4-%EC%84%B8%EC%85%98-%ED%86%A0%ED%81%B0-%EC%BA%90%EC%8B%9C-%EA%B7%B8%EB%A6%AC%EA%B3%A0-cdn/)



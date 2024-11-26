서비스를 개발하다 보면 실패에 따른 재수행 로직을 추가하고 싶어지는 때가 오는데, 이때 Spring Framwork 의 Retry 사용하면 어노테이션 기반으로 간편하게 재수행 로직을 추가할 수 있다.

# Retry Template VS Retry Annotation

spring retry 를 사용하는 방법에는

- 프로그래밍 방식 ( Retry Template )
- 선언적 방식 ( Retry Annotation ) 이 있다.

전자는 아래처럼 명시적으로 `RetryTemplate` 를 사용하여 Retry 를 실행할 callback 을 RetryTemplate 에 넘겨주는 방식이고,

```
@Service
class RetryableService {

    @Autowired
    private lateinit var retryTemplate: RetryTemplate

    fun run() : Unit {
        retryTemplate.execute<Unit, Throwable> {
           action()
        }
    }
}
```

[view raw](https://gist.github.com/HVHO/22a035816f597b8afbc5c17c266c6467/raw/cb8a7e87edb3d9d67028e939d61788cef2ab49bc/spring-retry-template.kt)[spring-retry-template.kt](https://gist.github.com/HVHO/22a035816f597b8afbc5c17c266c6467#file-spring-retry-template-kt) hosted with ❤ by [GitHub](https://github.com/)

후자는 Retry 를 적용할 method 에 `Retryable` 어노테이션을 적용시켜주면 스프링 AOP 에서 위임받아 Retry 를 적용시켜 주는 방식이다.

```
@Service
class RetryableService {

    @Retryable
    fun run() : Unit {
       action()
    }
}
```

[view raw](https://gist.github.com/HVHO/922cf53e07e9eaef30e3174fbea7ab73/raw/7cc9b392d1ed56107b21d533a391c5e7b2a68478/spring-retry-annotation.kt)[spring-retry-annotation.kt](https://gist.github.com/HVHO/922cf53e07e9eaef30e3174fbea7ab73#file-spring-retry-annotation-kt) hosted with ❤ by [GitHub](https://github.com/)

`RetryTemplate` 을 사용하면 RetryTemplate 에 대한 설정과, Retry 할 메소드를 직접 람다로 말아서 넣어줘야 하는 불편함 때문에 annoation 방식을 선호한다.




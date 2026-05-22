`@PostConstruct`
@PostConstruct는 의존성 주입이 이루어진 후 초기화를 수행하는 메서드이다. @PostConstruct가 붙은 메서드는 클래스가 service(로직을 탈 때? 로 생각 됨)를 수행하기 전에 발생한다. 이 메서드는 다른 리소스에서 호출되지 않는다해도 수행된다. 

출처: [https://zorba91.tistory.com/223](https://zorba91.tistory.com/223) [Carry On Progamming:티스토리]



## - Annotation 종류 및 의미

### @Target

@Targe은 Java Compiler가 어노테이션이 어디에 적용될지 결정하기 위해 사용됩니다.

아래 속성을 선언함에 따라 해당 어노테이션이 어떻게 선언할 때 사용되는 것인지 알려줍니다.

```
ElementType.PACKAGE         : 패키지 선언
ElementType.TYPE            : 타입 선언
ElementType.ANNOTATION_TYPE : 어노테이션 타입 선언
ElementType.CONSTRUCTOR     : 생성자 선언
ElementType.FIELD           : 멤버 변수 선언
ElementType.LOCAL_VARIABLE  : 지역 변수 선언
ElementType.METHOD          : 메서드 선언
ElementType.PARAMETER       : 전달인자 선언
ElementType.TYPE_PARAMETER  : 전달인자 타입 선언
ElementType.TYPE_USE        : 타입 선언
```

### @Retention

@Retention은 해당 어노테이션이 실제로 적용되고 유지되는 범위를 나타냅니다.

아래와 같은 종류의 타입이 있으며, 해당 타입을 통해 범위를 가져갑니다.

```
RetentionPolicy.RUNTIME : 컴파일 이후에도 JVM읠 통해 계속 참조가 가능. 대표적으로는 리플렉션이나 로깅에 사용
RetentionPolicy.CLASS   : 컴파일러가 클래스를 참조할 때까지만 유효
RetentionPolicy.SOURCE  : 컴파일 전까지만 유효. 컴파일 이후에는 사라지게 된다.
```

### @Documented

@Documented 어노테이션을 선언 시 사용한 클래스가 문서화될 경우 해당 어노테이션이 적용되었음을 명시하도록 한다.

### @Inherited

@Inherited 자식 클래스가 부모에 선언된 어노테이션을 같이 사용하고 싶을 때 선언합니다.

해당 어노테이션에 주석을 해석하면 아래와 같이 확인할 수 있습니다.

> @Inherited 어노테이션 가장 최상단 주석 설명  
>   
> Indicates that an annotation interface is automatically inherited  
> 어노케이션 인터페이스가 자동으로 상속됨을 나타낸다. 아래 더 자세한 설명을 하고 있다.  
>   
> If an Inherited meta-annotation is present on an annotation interface declaration, and the user queries the annotation interface on a class declaration, and the class declaration has no annotation for this interface, then the class's superclass will automatically be queried for the annotation interface.  
>   
> 어노테이션 인터페이스 선언에 상속된 메타 주석이 있고 사용자가 클래스 선언에 어노테이션 인터페이스를 쿼리하고 클래스 선언에 이 인터페이스에 대한 어노테이션이 없는 경우 클래스의 슈퍼 클래스가 어노테이션 인터페이스에 대해 자동으로 쿼리 합니다.  
>   
> 즉, "자동으로 상속 받는다"는 뜻입니다.

### @SpringBootConfiguration

@SpringBootConfiguration은 애플리케이션의 구성을 제공하는 어노테이션입니다.

해당 어노테이션을 확인하면 @Configuration과 @Indexed 어노테이션이 추가적으로 선언되어 있는 걸 확인할 수 있습니다.

#### @Configuration

사실 @SpringBootConfiguration은 @Configuration을 통해 @Bean을 생성하고 Spring Continer에 등록할 수 있습니다.

**@Configuartion은 앞으로 자주 사용되는 어노테이션입니다.(프로젝트 환경설정 시 사용!)**

#### @Indexed

@Indexed 어노테이션은 @Bean을 Spring Container에 등록할 때 색인화(인덱스 설정)와 스테레오 타입으로 설정합니다.

스테레오 타입(stereotype)이란 고정관념이라 해석되며 기본적으로 해당 어노테이션을 선언한 인터페이스를 상속(extends)또는 구현(implements)할 경우 자동으로 기능들이 포함됩니다.

@Indexed 어노테이션을 주석을 확인하면 예시가 있습니다. (더보기를 클릭해서 확인해보세요.)

더보기

예시를 해석하면 아래와 같이 해석할 수 있습니다.

```
@Indexed
 public interface AdminService { ... }
 
 public class ConfigurationAdminService implements AdminService { ... }
```

ConfigurationAdminService 클래스는 인덱싱 된 인터페이스를 구현(implements) 하기 때문에 stereotype으로 AdminService 인터페이스를 자동으로 포함된다. (stereotype: 고정관념)

또한, 클래스 계층구조에서 여러 인터페이스 또는 슈퍼 클래스가 있는 경우 클래스는 모든 고정관념에 매핑된다.(포함된다는 뜻)

### @EnableAutoConfiguration

@EnableAutoConfiguration 어노테이션은 base package로 정의된 경로의 모든 Bean을 자동으로 구성합니다.

즉, @SpringBootApplication 어노테이션이 @EnableAutoConfiguration을 선언해 사용하고 있기 때문에 @SpringBootApplication 기준으로 package를 모든 Bean으로 자동 구성하는 겁니다.

**그래서 가장 최상위 패키지에 선언되어 있는 것입니다.**

만약 구성하고 싶지 않다면, exclued 또는 excludeName을 통해 제외시킬 수 있습니다.

### @Import

@Import 어노테이션은 @Configuration으로 설정한 설정 파일을 두 개 이상 사용 시 그룹으로 묶어 사용할 수 있게 해주는 어노테이션입니다.

기본적으로 하나의 Configuration 설정 시 아래와 같이 사용됩니다.

```
@Configuration
public class AppConfig {

    @Bean
    public UserRepositoryInterface userRepository(){
        return new UserMemoryRepository();
    }
}
```

@Import 어노테이션을 사용하면 아래와 같이 사용할 수 있습니다.

```
@Configuration
@Import({MultiAppConfig.NumberOneAppConfig.class, MultiAppConfig.NumberTwoAppConfig.class})
public class MultiAppConfig {

    @Configuration
    static class NumberOneAppConfig {

        @Bean
        public UserRepositoryInterface userMemoryRepository() {
            return new UserMemoryRepository();
        }

    }

    @Configuration
    static class NumberTwoAppConfig {

        @Bean
        public UserRepositoryInterface userDiskRepository() {
            return new UserDiskRepository();
        }
    }
}
```

### @ComponentScan

@ComponentScan 어노테이션은 @Component 어노테이션을 명시한 클래스들을 Scan 하여 해당 클래스를 Bean으로 만들어 Spring Continaer에 등록합니다.

다른 시간에 설명하겠지만 수동으로 @Bean 어노테이션을 사용해서 Spring Container에 Bean을 등록할 수 있습니다.

하지만 Spring Boot 프레임워크를 사용하면 기본적으로 많이 사용하는 것들은 자동으로 설정할 수 있게 어노테이션을 제공합니다.

지난 시간 프로젝트 코드를 확인하면 @Controller, @Service, @Repository가 있는 걸 확인할 수 있습니다.

[[Spring Boot] Spring Boot API 만들기 (3) - @Controller, @Service, @Repository 구조 설정](https://any-ting.tistory.com/138)

 [[Spring Boot] Spring Boot API 만들기 (3) - @Controller, @Service, @Repository 구조 설정

- 지난 시간 안녕하세요. 지난 시간에는 계층 구조(Layered Architecture)에 대해 알아봤습니다. 혹시 놓치고 오신 분들은 아래 링크를 통해 학습하고 오시는 걸 추천드리겠습니다. [Spring Boot] Spring Boot

any-ting.tistory.com](https://any-ting.tistory.com/138)

Spring Boot는 이렇게 개발자가 귀찮을 부분들을 최소화 시키 기능을 제공해줍니다. (생상성이 빠른다는 부분이 어느 정도 느껴지시나요?)

또한, @SpringBootApplication 어노테이션에 선언된 @ComponentScan을 확인하면 @Filter 어노테이션을 확인할 수 있습니다.

```
@ComponentScan(excludeFilters = {
 @Filter(type = FilterType.CUSTOM, classes = TypeExcludeFilter.class),
 @Filter(type = FilterType.CUSTOM, classes = AutoConfigurationExcludeFilter.class)})
```

excludeFilters는 스캔 대상을 제외하고 싶을 때 사용하며, Filter 어노테이션을 선언해 필터링할 정보를 작성합니다.

@Filters 어노테이션은 아래와 같이 제외대상과 추가 대상을 설정할 수 있게 옵션을 제공합니다.

1. inculedFillters : ComponentScan 대상을 추가로 지정
2. excludeFilters : ComponentScan에서 제외할 대상을 지정

또한, FilterType에는 다섯 가지 타입을 설정할 수 있습니다.

1. ANNOTATION : 어노테이션을 인식해서 동작하며, 기본으로 설정되는 값입니다.
2. ASSIGNABLE_TYPE : 지정한 타입과 자식 타입을 인식해서 동작합니다. 특정 클래스를 지정해서 사용합니다. 또한 자식 클래스까지 타입을 인식해서 동작합니다.
3. ASPECTJ : AspectJ 패턴을 통해 인식합니다.
4. REGEX : 정규 표현식을 사용해서 인식합니다.
5. CUSTOM : TypeFilter라는 인터페이스를 구현해서 인식합니다.


출처 : https://any-ting.tistory.com/143
**리플렉션이란?**

- 리플렉션은 자바에서 클래스나 멤버에 대한 정보를 런타임에 조사하고, 조작할 수 있는 기능이다. 
- 예를 들어, 클래스의 이름, 메서드, 필드, 생성자 등에 대한 정보를 프로그램 실행 중에 알아내고, 이를 통해 객체를 생성하거나 메서드를 호출할 수 있다. 이 기능 덕분에, 개발자는 코드의 유연성과 확장성을 높일 수 있다.  




리플렉션을 활용한 기능 중 하나 : DI


**리플렉션 예시**

- 코드를 보면 Class.forName("java.lang.String")은 String 클래스에 대한 Class 객체를 가지고 온다. 그리고 getDeclaredMethods() 메서드를 사용해서 가져온 클래스에 정의된 모든 메서드의 정보를 얻어내는 것이다. 이렇게 리플렉션을 활용하면, 런타임(Runtime)에 동적으로 클래스의 정보를 얻어내고, 이를 바탕으로 다양한 작업을 할 수 있다.

```java
CopyClass<?> clazz = Class.forName("java.lang.String");
Method[] methods = clazz.getDeclaredMethods();

for (Method method : methods) {
    System.out.println(method.getName());
}
```

출처: [https://curiousjinan.tistory.com/entry/java-reflection-explain](https://curiousjinan.tistory.com/entry/java-reflection-explain) [오늘도 개발중입니다:티스토리]



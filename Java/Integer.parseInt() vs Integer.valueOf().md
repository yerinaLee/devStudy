|메서드|리턴 타입|설명|
|---|---|---|
|`Integer.parseInt(String s)`|`int` (기본형)|문자열을 **기본형 int**로 변환함.|
|`Integer.valueOf(String s)`|`Integer` (참조형)|문자열을 **Integer 객체**로 변환함. 내부적으로 `parseInt()`를 호출하고, 그 결과를 **캐싱된 Integer 객체**로 감쌈.|
- `valueOf()`는 [Integer 캐싱 범위](https://docs.oracle.com/javase/8/docs/api/java/lang/Integer.html#valueOf-int-)인 **-128 ~ 127** 내의 숫자는 기존 객체를 재사용하기 때문에 메모리 효율에 조금 더 좋을 수 있어요.
: Java에서 `Integer.valueOf(int i)`를 사용할 때, 값이 **-128에서 127 사이**라면, **새 객체를 생성하지 않고** **미리 캐싱된 Integer 객체**를 재사용합니다.


캐싱범위 : https://velog.io/@chullll/JAVA-Integer-Caching

- `parseInt()`는 기본형 `int`를 리턴하므로, 오토박싱이 필요한 경우엔 `valueOf()`가 더 깔끔함.

---

### ✅ 결론

- 기본형 `int`가 필요하다면 `parseInt()`.
- `Integer` 객체가 필요하거나, 박싱이 필요한 상황이면 `valueOf()`.


```
String str = "123";

int a = Integer.parseInt(str);       // a는 int
Integer b = Integer.valueOf(str);    // b는 Integer (객체)

```
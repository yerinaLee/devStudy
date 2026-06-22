

### String  vs StringBuffer / StringBuilder
---
- StringBuffer, StringBuilder는 문자열 연산 전용 자료형. 모두 문자열을 연산할때 주로 사용 
-  String도 concat() or + 연산으로 이어붙이기가 가능하지만, 내용이 합쳐진 String 인스턴스를 생성하면서 메모리 공간이 낭비됨
ㄴ 여기서 기존 String객체는 GC 제거 대상이 됨
ㄴ 빈번하게 Minor GC를 일으켜 Full GC(Major Gc)를 일으키는 원인이 될 수 있음


String은 불변 자료형. 한 번 할당된 공간이 변하지 않음
> jdk 8 까지는 String 객체의 값은 char 배열로 구성되어 있음
> jdk 9부터 기존 char 배열에서 byte 배열을 사용하여 String Compacting을 통한 성능 및 heap 공간 효율(2byte -> 1byte)을 높이도록 수정됨


StringBuffer, StringBuilder 는 가변 자료형
-> 문자열을 수정할 때 동일 객체 내에서 변경이 가능하다.

두 클래스는 사용 문법이 같음



### StringBuffer vs StringBuilder
---
StringBuffer에서 `synchronized` 키워드를 사용하기 때문에 멀티 스레드에서 동시에 객체에 접근할때 변조방지가 가능함
-> StringBuffer가 멀티쓰레드 환경에서 더 안전

> java에서 synchronized 키워드는 여러개의 스레드가 한 개의 자원에 접근할려고 할 때, 현재 데이터를 사용하고 있는 스레드를 제외하고 나머지 스레드들이 데이터에 접근할 수 없도록 막는 역할을 수행한다.




### StringBuffer
- 기본 StringBuffer 버퍼 크기는 16개 문자 저장 가능
```
StringBuffer sb = new StringBuffer(); 
// new StringBuffer() 인수에 아무것도 넣어주지 않으면 기본 16으로 배열 길이를 잡음
```



- StringBuilder가 StringBuffer보다 조금 더 빠르지만 멀티쓰레드 환경에서 안전해야하기때문에 StringBuffer 사용 추천!


## 최종 결론

- **String 을 사용해야 할 때 :**
    - String은 불변성
    - ==문자열 연산이 적고 변하지 않는 문자열을 자주 사용할 경우==
    - 멀티쓰레드 환경일 경우 
    
- **StringBuilder 를 사용 해야 할 때 :**
    - StringBuilder는 가변성
    - 문자열의 추가, 수정, 삭제 등이 빈번히 발생하는 경우
    - 동기화를 지원하지 않아, 단일 쓰레드이거나 동기화를 고려하지 않아도 되는 경우
    - 속도면에선 StringBuffer 보다 성능이 좋다.
    
- **StringBuffer 를 사용해야 할 때 :**
    - StringBuffer는 가변성
    - ==문자열의 추가, 수정, 삭제 등이 빈번히 발생하는 경우
    - ==동기화를 지원하여, 멀티 스레드 환경에서도 안전하게 동작



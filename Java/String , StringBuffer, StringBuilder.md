

### 문자열 연산 전용 자료형
---
- StringBuffer, StringBuilder는 모두 문자열을 연산할때 주로 사용 
-  String도 concat() or + 연산으로 이어붙이기가 가능하지만, 내용이 합쳐진 String 인스턴스를 생성하면서 메모리 공간이 낭비됨
ㄴ 여기서 기존 String객체는 GC 제거 대상이 됨
ㄴ 빈번하게 Minor GC를 일으켜 Full GC(Major Gc)를 일으키는 원인이 될 수 있음




### StringBuffer
- 기본 StringBuffer 버퍼 크기는 16개 문자 저장 가능
```
StringBuffer sb = new StringBuffer(); 
// new StringBuffer() 인수에 아무것도 넣어주지 않으면 기본 16으로 배열 길이를 잡음
```


String은 불변 자료형. 한 번 할당된 공간이 변하지 않음
> jdk 8 까지는 String 객체의 값은 char 배열로 구성되어 있음
> jdk 9부터 기존 char 배열에서 byte 배열을 사용하여 String Compacting을 통한 성능 및 heap 공간 효율(2byte -> 1byte)을 높이도록 수정됨


StringBuffer, StringBuilder 는 가변 자료형
-> 문자열을 수정할 때 동일 객체 내에서 변경이 가능하다.

두 클래스는 사용 문법이 같음

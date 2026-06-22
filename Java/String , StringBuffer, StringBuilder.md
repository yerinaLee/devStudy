

### 문자열 연산 전용 자료형
---
- StringBuffer, StringBuilder는 모두 문자열을 연산할때 주로 사용 
> String도 concat() or + 연산으로 이어붙이기가 가능하지만, 내용이 합쳐진 String 인스턴스를 생성하면서 메모리 공간이 낭비됨



### StringBuffer
- 기본 StringBuffer 버퍼 크기는 16개 문자 저장 가능
- 


String은 불변 자료형. 한 번 할당된 공간이 변하지 않음
> jdk 8 까지는 String 객체의 값은 char[] 배열로 구성되어져 있지만, jdk 9부터 기존 char[]에서 byte[]을 사용하여 String Compacting을 통한 성능 및 heap 공간 효율(2byte -> 1byte)을 높이도록 수정되었다.

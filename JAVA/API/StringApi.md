# String Api💻

### String 관련 클래스

* String 클래스  
  > 문자열 값 수정 불가능, immutable(불변)  
  > 수정시 수정된 문자열이 새로 할당 되어 새 주소를 넘김
* StringBuffer 클래스
  > 문자열 값 수정 가능, mutable(가변)  
  > 수정, 삭제 등이 기존 문자열에 수정되어 적용  
  > 기본 16문자 크기로 지정된 버퍼를 이용하며 크기 증가 가능  
  > 쓰레드 safe기능 제공(성능 저하 요인)
* StringBuilder 클래스
  > StringBuffer와 동일하나 쓰레드 safe기능을 제공하지 않음

String은 불변성을 가졌기 때문에 .concat혹은 +를 이용한 값변경은 기존 String에 들어있던 값을 버리고 새로운 값을 할당하는 것이다.  
따라서 .concat혹은 +를 많이사용하는 경우 속도가 느려져 비효율적이다.  
StringBuffer나 StringBuilder는 값을 변경할수 있기 때문에 문자열 연산(추가, 수정)이 빈번하다면 StringBuffer/StringBuilder를 사용하면 된다.'

### String 클래스

* String.hashCode():int
```JAVA
String str = "JAVA"
System.out.println(str.hashCode());
```

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

* concat(Strig str):String -> 문자열 뒤에 문자열 추가하는 메소드
```JAVA
String str = "JAVA"
String concatStr = str.concat("!!!");
System.out.println(concatStr);  // JAVA!!!출력
```
* substring(int beginIndex):String -> beginIndex위치 부터 끝까지 문자열 반환
```JAVA
String str = "ABCDEFGHIJ";
System.out.println(str.substring(6)); // GHIJ 출력
```

* substring(int beginIndex, int endIndex):String -> beginIndex 위치 부터 endIndex 전 위치까지 문자열 반환
```JAVA
String str = "ABCDEFGHIJ";
System.out.println(str.substring(3, 7)); // DEFG 출력
```

* replace(char oldChar, char newChar):String -> 문자열에 있는 모든 oldChar를 newChar로 변환
```JAVA
String str = "AOBOCODOEOF";
System.out.println(str.replace('O', 'I')); // AIBICIDIEIF 출력
```

* equalsIgnoreCase(String anotherString):bolean -> 문자열과 anotherString 대소문자 관계없이 비교
```JAVA
String str = "ABCDEFGH";
System.out.println(str.equalsIgnoreCase("abcdefgh)); // true
```

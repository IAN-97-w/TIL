# String Api💻

### String 관련 클래스

- String 클래스
  > 문자열 값 수정 불가능, immutable(불변)  
  > 수정시 수정된 문자열이 새로 할당 되어 새 주소를 넘김
- StringBuffer 클래스
  > 문자열 값 수정 가능, mutable(가변)  
  > 수정, 삭제 등이 기존 문자열에 수정되어 적용  
  > 기본 16문자 크기로 지정된 버퍼를 이용하며 크기 증가 가능  
  > 쓰레드 safe기능 제공(성능 저하 요인)
- StringBuilder 클래스
  > StringBuffer와 동일하나 쓰레드 safe기능을 제공하지 않음

String은 불변성을 가졌기 때문에 .concat혹은 +를 이용한 값변경은 기존 String에 들어있던 값을 버리고 새로운 값을 할당하는 것이다.  
따라서 .concat혹은 +를 많이사용하는 경우 속도가 느려져 비효율적이다.  
StringBuffer나 StringBuilder는 값을 변경할수 있기 때문에 문자열 연산(추가, 수정)이 빈번하다면 StringBuffer/StringBuilder를 사용하면 된다.'

---

### String 클래스

- concat(Strig str):String -> 문자열 뒤에 문자열 추가

```JAVA
String str = "JAVA"
String concatStr = str.concat("!!!");
System.out.println(concatStr);  // JAVA!!!출력
```

- substring(int beginIndex):String -> beginIndex위치 부터 끝까지 문자열 반환

```JAVA
String str = "ABCDEFGHIJ";
System.out.println(str.substring(6)); // GHIJ 출력
```

- substring(int beginIndex, int endIndex):String -> beginIndex 위치 부터 endIndex 전 위치까지 문자열 반환

```JAVA
String str = "ABCDEFGHIJ";
System.out.println(str.substring(3, 7)); // DEFG 출력
```

- replace(char oldChar, char newChar):String -> 문자열에 있는 모든 oldChar를 newChar로 변환

```JAVA
String str = "AOBOCODOEOF";
System.out.println(str.replace('O', 'I')); // AIBICIDIEIF 출력
```

- equalsIgnoreCase(String anotherString):bolean -> 문자열과 anotherString 대소문자 관계없이 비교

```JAVA
String str = "ABCDEFGH";
System.out.println(str.equalsIgnoreCase("abcdefgh")); // true 출력
```

- trim():String -> 문자열의 앞뒤 모든 공백 제거

```JAVA
String str = "   AB C  E       ";
System.out.println(str.trim()); // AB C  E 출력
```

- split(String regex):String[] -> 문자열에 있는 regex를 기준으로 문자열을 잘라 String 배열로 반환

```JAVA
String str = "A,B,C,D,E,F";
String[] Arr = str.split(",");
System.out.println(Arr[0]); //  A 출력
System.out.println(Arr[1]); //  B 출력
System.out.println(Arr[2]); //  C 출력
System.out.println(Arr[3]); //  D 출력
System.out.println(Arr[4]); //  E 출력
System.out.println(Arr[5]); //  F 출력
```

---

### StringBuffer 클래스

- StringBuffer.append(String str):StringBuffer -> 문자열 뒤에 문자열 추가

```JAVA
StringBuffer buffer = new StringBuffer("JAVA");
System.out.println(buffer.append("!!!"));  // JAVA!!!출력
```

- StringBuffer.insert(int offset, String str):StringBuffer -> 문자열의 offset번째 인덱스에 str 삽입

```JAVA
StringBuffer buffer = new StringBuffer("JAVA");
System.out.println(buffer.insert(2, "ooo"));  // JAoooVA출력
```

- StringBuffer.delete(int start, int end):StringBuffer -> 문자열의 start번째 인덱스부터 end번째 전 인덱스까지 삭제

```JAVA
StringBuffer buffer = new StringBuffer("JAVA");
System.out.println(buffer.delete(2, 4));  // JA출력
```

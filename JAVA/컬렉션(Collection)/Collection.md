# 💻 컬렉션(Collection)

## ✏️ 컬렉션

자바에서 자료구조를 담당하는 프레임워크  
추가, 삭제, 정렬 등의 기능처리가 간단하게 해결 되어 자료구조적 알고리즘을 구현할 필요 없음

### 자료구조

데이터를 메모리에서 구조적으로 처리하는 방법론  
 ![자료구조](https://user-images.githubusercontent.com/105089699/183848277-9259a55d-a708-49e7-8429-bb9714f4da4f.png)

### 배열의 문제점

1. 한 번 크기를 지정하면 변경할 수 없다.
   필요에 따리 공간을 늘리거나 줄일 수 없음  
   공간 크기가 부족하면 에러가 발생  
   -> 할당 시 넉넉한 크기로 할당하게 됨 (메모리 낭비)
2. 기록된 데이터에 대한 중간 위치의 추가, 삭제가 불편하다.
   추가, 삭제할 데이터부터 마지막 기록된 데이터까지 하나씩 뒤로 밀어내고 추가해야 함 (복잡한 알고리즘)
3. 한 타입의 데이터만 저장 가능하다

### 컬렉션의 장점

1. 저장하는 크기의 제약이 없다.
2. 추가, 삭제, 정렬 등의 기능 처리가 간단하게 해결된다.
   자료를 구조적으로 처리 하는 자료구조가 내장되어 있어 알고리즘 구현이 필요 없음
3. 여러 타입으 데이터가 저장 가능하다.
   객체만 저장할 수 있기 때문에 필요에 따리 기본 자료형을 저장해야 하는 경우 Wrapper클래스 사용  
   **여러 타입의 데이터가 저장 가능하지만 실제로 거의 한가지 타입의 데이터만 저장한다.**

### 컬렉션의 주요 인터페이스

![컬렉션의 주요 인터페이스](https://user-images.githubusercontent.com/105089699/183849920-cbfc9cca-ddab-4941-9838-5a8765788f19.png)
**List와 Set은 Collection을 상속받고 있어 메소드 구조가 비슷하다.**

---

## ✏️ List

자료들을 순차적으로 나열한 자료구조로 인덱스로 관리되며, 중복해서 객체 저장 가능
![list](https://user-images.githubusercontent.com/105089699/183850743-3059cf42-f92d-41d1-9c86-a4763675bc83.png)

### List 계열 주요 메소드

![list 메소드](https://user-images.githubusercontent.com/105089699/183851232-636e271d-4625-48eb-903a-1977d425413b.png)

### ArrayList

List의 후손으로 초기 저장용량은 10으로 자동 설정  
저장 용량을 초과한 객체들이 들어오면 자동으로 증가  
순서를 유지하고 저장하고 중복 저장이 가능  
**List중에 가장 많이 사용됨**

```JAVA
ArrayList<String> list = new ArrayList<String>(3);
	   // 제네릭(타입 설정), 제네릭을 설정하지 않으면 모든 타입 저장 가능

		// add(String e) -> 객체 추가(list의 제네릭을 String으로 설정했기때문에 add의 파라미터도 String)
		list.add("문자열");
		list.add("도대담");
		list.add("남나눔");
		System.out.println(list);	// [문자열, 도대담, 남나눔] 출력

		list.add("하현호");	// ArrayList의 저장용량이 꽉찼지만 객체 추가시 저장용량도 늘어남
		System.out.println(list);	// [문자열, 도대담, 남나눔, 하현호] 출력
		// size():int -> 현재 list에 담긴 element 개수 반환
		System.out.println(list.size()); //	4 출력

		// add(int index, String element) -> index위치에 객체 삽입
		list.add(0, "류라라");
		System.out.println(list); // [류라라, 문자열, 도대담, 남나눔, 하현호] 출력

		list.add(3,"강건강");
		System.out.println(list); // [류라라, 문자열, 도대담, 강건강, 남나눔, 하현호] 출력

		// remove(int index) -> index위치 객체 삭제
		list.remove(1);
		System.out.println(list); // [류라라, 도대담, 강건강, 남나눔, 하현호] 출력
		// remove(Object o) -> 특정 객체 삭제
		list.remove("류라라");
		System.out.println(list); // [도대담, 강건강, 남나눔, 하현호] 출력

		// Collections : Collection에서 유용한 메소드들을 모아놓은 클래스
		// sort(List<String> list) -> 오름차순 정렬
		Collections.sort(list);
		System.out.println(list); // [강건강, 남나눔, 도대담, 하현호]출력

		// set(int index, String element):String -> index위치 객체 element로 변경
		list.set(3, "박보배");
		System.out.println(list); // [강건강, 남나눔, 도대담, 박보배] 출력

		// get(int index):String // index위치 객체 가져오기
		System.out.println(list.get(2)); //	도대담 출력

		// contains(Object o):boolean -> 리스트안에 객체가 있는지 확인
		boolean bool = list.contains("류라라");
		System.out.println(bool); // false 출력

		// indexOf(Object o):int -> 리스트에서 객체가 몇번째 index에 있는지 반환
		int index1 = list.indexOf("도대담");
		System.out.println(index1); // 2 출력

		// clear() -> 리스트안의 객체 전부 제거
		list.clear();
		System.out.println("list : " + list); // [] 출력
		// isEmpty():boolean -> 리스츠가 비었는지 확인
		System.out.println(list.isEmpty()); // true
```

### Vector

List의 후손으로 ArrayList와 동등하지만 동기화를 제공한다는 점이 ArrayList와의 차이점  
-> List 객체들 중에서 가장 성능이 좋지 않아 거의 사용 하지 않음

### LinkedList

List의 후손으로, 인접 참조를 링크해 체인처럼 관리  
특정 인덱스에서 객체를 제거하거나 추가하게 되면 바로 앞 / 뒤 링크만 변경하면 되기 때문에 객체 삭제와 삽입이 빈번하게 일어나는 곳에서는 ArrayList보다 성능이 좋음

---

## ✏️ Set

저장 순서가 유지되지 않고, 중복 객체도 저장하지 못하게 하는 자료 구조 null도 중복을 허용하지 않기 때문에 1개의 null만 저장

![set](https://user-images.githubusercontent.com/105089699/183860663-bf4c7e91-ded9-4029-843f-bc97dd4c32c5.png)

### Set 계열 주요 메소드

![set](https://user-images.githubusercontent.com/105089699/183860981-00d8bacd-357a-47ac-8d7e-e6c9ddd48fea.png)

- HashSet
  Set에 객체를 저장할 떄 hash함수를 사용하여 처리 속도가 빠름  
   동일 객체 뿐 아니라 동등 객체도 중복하여 저장하지 않음  
   **동일 객체 : 주소값까지 같은 것  
  동등 객체 : 주소값은 다르나 내용은 같은 것**
- LinkedHashSet
  HashSet과 거의 동일하지만  
  Set에 추가되는 순서를 유지한다는 점이 다름

### Iterator

컬렉션에 저장된 요소를 접근하는데 사용되는 인터페이스

- Enumeration : Iterator의 구버전
- ListItretator : Iterator를 상속받아 양방향 특징
  ![Iterator](https://user-images.githubusercontent.com/105089699/184042901-69e39026-f333-4142-91bd-44d685a771c7.png)

---

## ✏️ Map

Key와 Value로 구성되어 있으며, 키와 값은 모두 객체  
키는 중복 저장을 허용하지 않고(Set방식, 순서유지 불가), 값은 중복 저장 가능(List방식)  
키가 중복되는 경우, 기존에 있는 키에 해당하는 값을 덮어 씌움  
**Key와 Value의 쌍을 Entry라고 부른다**

![map](https://user-images.githubusercontent.com/105089699/184044557-efde1e08-86c7-4029-942e-edaacb68bf01.png)

### Map의 메소드

![map 메소드](https://user-images.githubusercontent.com/105089699/184044833-e3ce9351-ea7b-423a-b327-f756cedeea44.png)

### HashMap

키 객체는 hashCode()와 equals()를 재정의해 동등 객체가 될 조건을 정해야함, 때문에 키 타입은 hashCOde와 equals()메소드가 재정의 되어있는 string타입을 주로 사용

### Hasshtable

HashMap의 구버전  
키 객체 만드는 법은 HashMap과 동일하나 Hashtable은 쓰레드 동기화가 된 상태이기 때문에, 복수의 쓰레드가 동시에 Hashtable에 접근해 객체를 추가, 삭제 하더라도 쓰레드에 안전

### Properties

키와 값을 String타입으로 제한한 Map컬렉션  
주로 Properties느 프로퍼티(\*.properties)파일을 읽어 들일 때 주로 사용

#### 프로퍼티(\*.properties)파일

- 옵션정보, 데이터베이스 연결정보, 국제화정보를 기록하여 텍스트 파일로 활용
- 애플리케이션에서 주로 변경이 잦은 문자열을 저장하여 관리하기 때문에 유지보수를 편리하게 만들어줌
- 키와 값이 '='기호로 연결되어 있는 텍스트 파일로 ISO 8859-1 문자셋으로 저장되고, 한글은 유니코드로 변환되어 저장

```JAVA
HashMap<String, Snack> map = new HashMap<>();
				// 타입 추론
// put(K key, V value):V -> 맵에 key와 value 추가(key의 전 vlaue 반환)
map.put("새우깡", new Snack("짠맛", 1500));
map.put("다이제", new Snack("단맛", 2500));
map.put("포테이토칩", new Snack("짠맛", 1500));
map.put("고소미", new Snack("고소한맛", 1000));
System.out.println(map); // {다이제=단맛[2500원], 새우깡=짠맛[1500원], 포테이토칩=짠맛[1500원], 고소미=고소한맛[1000원]} 출력

map.put("새우깡", new Snack("매운맛", 1500)); // 중복저장이 불가능, 덮어쓰기
System.out.println(map); // {다이제=단맛[2500원], 새우깡=매운맛[1500원], 포테이토칩=짠맛[1500원], 고소미=고소한맛[1000원]} 출력

// containsKey(Object key):boolean -> 맵에 특정 key가 있는지 확인
System.out.println(map.containsKey("새우깡")); // true 출력

// containsValue(Object value):boolean -> 맵에 특정 value가 있는지 확인 (equals메소드 오버라이딩 해야함)
System.out.println(map.containsValue(new Snack("짠맛", 1500))); // true 출력

// get(Object key):V -> 맵에 특정 key의 value를 반환(존재하지 않으면 null 반환)
Snack get1 = map.get("새우깡"); // 매운맛[1500원] 반환
System.out.println(get1);
Snack get2 = map.get("홈런볼");
System.out.println(get2); // null 반환

// keySet():Set<K> -> map에 있는 모든 key를 Set에 담아 반환
Set<String> set1 = map.keySet();
System.out.println(set1);
Iterator<String> it1 = set1.iterator();
while(it1.hasNext()) {
	String key = it1.next();
	Snack value = map.get(key);
	System.out.println(key + " : " + value); // 맵의 모든 key와 value 출력
}

// entrySet():set<Entry<K, V>> -> 모든 entry를 set에 담아 반환
Set<Entry<String, Snack>> set2 = map.entrySet();
System.out.println(set2);
Iterator<Entry<String, Snack>> it2 = set2.iterator();
while(it2.hasNext()) {
	Entry<String, Snack> entry = it2.next();
	String key = entry.getKey();
	Snack value = entry.getValue();
	System.out.println(key + " : " + value); // 맵의 모든 key와 value 출력
}
```

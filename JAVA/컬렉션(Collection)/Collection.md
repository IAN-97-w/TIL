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
		// isEmpty():boolean
		System.out.println(list.isEmpty()); // true
```

ArrayList 주로 사용  
Vector - ArrayList의 구버전 요즘 거의 사용 안함  
LinkedList - 수정이 빈번하게 일어날때 사용

프레임워크 - 목적에 따라 효율적으로 구조를 짜놓는 개발 방식

## ✏️ Set

동일 객체 : 주소값까지 같은 것  
동등 객체 : 주소값은 다르나 내용은 같은 것

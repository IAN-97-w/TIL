# 💻 Date API

## ✏️ 날짜 관련 클래스

- Date 클래스

  > 시스템으로부터 현재 날짜, 시간 정보를 가져와서 다룰 수 있게 만들어진 클래스  
  > 생성자 2개만 사용 가능하고 나머지는 모두 deprecated
  > Calendar 클래스 혹은 GregorianCalendar 클래스 사용 권장

- Calendar 클래스

  > Calendar클래스는 생성자가 protected이기 때문에 new연산자를 통해 객체 생성 불가능  
  > getInstance() 메소드를 통해서 객체 생성

- GregorianCalendar 클래스

  > GregorianCalendar클래스는 Calendar클래스의 후손 클래스
  > 년, 월, 일, 시, 분, 초 정보를 필드를 이용하여 다룰 수 있음

---

## ✏️ Date 클래스

- Date() 생성자

```JAVA
Date date = new Date();
System.out.println(date);   //  현재 날짜, 시간 출력 ex)Sun Aug 07 11:01:27 KST 2022
```

- getTime():long -> 현재시간을 long값으로 반환

```JAVA
Date date = new Date();
System.out.println(date.getTime()); //  현재 날짜, 시간의 long값 출력 ex) 1659670277589
```

- Date(long date) 생성자

```JAVA
Date longDate = new Date(1659670277589);
System.out.println(longDate);   //  long값을 반환받은 날짜, 시간 출력 ex) Fri Aug 05 12:31:17 KST 2022
```

이외 생성자는 사용 권장하지 않음

---

## ✏️ Calendar 클래스

- getInstance():Calendar -> Calendar는 생성자가 protected이기 때문에 new연산자를 통해 객체 생성 불가능하기 때문에 getInstance() 메소드를 통해서 객체 생성

```JAVA
Calendar c = Calendar.getInstance(); // Calendar 객체 생성
```

- get(int field):int -> 입력한 field(ex) Calendar.YEAR(년도))의 값 반환

```JAVA
System.out.println(c.get(Calendar.YEAR)); // 현재 년도 반환

System.out.println(c.get(Calendar.MONTH)); // 현재 월 반환

System.out.println(c.get(Calendar.DATE)); // 현재 일 반환

System.out.println(c.get(Calendar.AM_PM)); // 오전이면 0 오후면 1 반환

System.out.println(c.get(Calendar.HOUR)); // 현재  시간 반환(12시간 기준)

System.out.println(c.get(Calendar.HOUR_OF_DAY)); //  현재  시간 반환 (24시간 기준)

System.out.println(c.get(Calendar.AM_PM)); // 오전이면 0 오후면 1 반환

System.out.println(c.get(Calendar.MINUTE)); // 현재 분 반환

System.out.println(c.get(Calendar.SECOND)); // 현재 초 반환

System.out.println(c.get(Calendar.DAY_OF_WEEK)); //  요일 반환 (일 = 1 ..... 토 =7)
```

---

## ✏️ GregorianCalendar 클래스

- GregorianCalendar​(int year, int month, int dayOfMonth, int hourOfDay, int minute, int second) -> 년, 월, 일, 시, 분, 초를 입력받는 생성자

```JAVA
GregorianCalendar gc = new GregorianCalendar(2022, 0, 1, 1, 1, 1);

System.out.println(gc.get(Calendar.YEAR)); // 2022 출력
System.out.println(gc.get(Calendar.MONTH)); // 1 출력 (0인덱스부터 시작하기 때문에 입력할때 -1해줘야 함)
System.out.println(gc.get(Calendar.DAY)); // 1 출력
```

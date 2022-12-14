# ๐ป Date API

## โ๏ธ ๋ ์ง ๊ด๋ จ ํด๋์ค

- Date ํด๋์ค

  > ์์คํ์ผ๋ก๋ถํฐ ํ์ฌ ๋ ์ง, ์๊ฐ ์ ๋ณด๋ฅผ ๊ฐ์ ธ์์ ๋ค๋ฃฐ ์ ์๊ฒ ๋ง๋ค์ด์ง ํด๋์ค  
  > ์์ฑ์ 2๊ฐ๋ง ์ฌ์ฉ ๊ฐ๋ฅํ๊ณ  ๋๋จธ์ง๋ ๋ชจ๋ deprecated
  > Calendar ํด๋์ค ํน์ GregorianCalendar ํด๋์ค ์ฌ์ฉ ๊ถ์ฅ

- Calendar ํด๋์ค

  > Calendarํด๋์ค๋ ์์ฑ์๊ฐ protected์ด๊ธฐ ๋๋ฌธ์ new์ฐ์ฐ์๋ฅผ ํตํด ๊ฐ์ฒด ์์ฑ ๋ถ๊ฐ๋ฅ  
  > getInstance() ๋ฉ์๋๋ฅผ ํตํด์ ๊ฐ์ฒด ์์ฑ

- GregorianCalendar ํด๋์ค

  > GregorianCalendarํด๋์ค๋ Calendarํด๋์ค์ ํ์ ํด๋์ค
  > ๋, ์, ์ผ, ์, ๋ถ, ์ด ์ ๋ณด๋ฅผ ํ๋๋ฅผ ์ด์ฉํ์ฌ ๋ค๋ฃฐ ์ ์์

---

## โ๏ธ Date ํด๋์ค

- Date() ์์ฑ์

```JAVA
Date date = new Date();
System.out.println(date);   //  ํ์ฌ ๋ ์ง, ์๊ฐ ์ถ๋ ฅ ex)Sun Aug 07 11:01:27 KST 2022
```

- getTime():long -> ํ์ฌ์๊ฐ์ long๊ฐ์ผ๋ก ๋ฐํ

```JAVA
Date date = new Date();
System.out.println(date.getTime()); //  ํ์ฌ ๋ ์ง, ์๊ฐ์ long๊ฐ ์ถ๋ ฅ ex) 1659670277589
```

- Date(long date) ์์ฑ์

```JAVA
Date longDate = new Date(1659670277589);
System.out.println(longDate);   //  long๊ฐ์ ๋ฐํ๋ฐ์ ๋ ์ง, ์๊ฐ ์ถ๋ ฅ ex) Fri Aug 05 12:31:17 KST 2022
```

์ด์ธ ์์ฑ์๋ ์ฌ์ฉ ๊ถ์ฅํ์ง ์์

---

## โ๏ธ Calendar ํด๋์ค

- getInstance():Calendar -> Calendar๋ ์์ฑ์๊ฐ protected์ด๊ธฐ ๋๋ฌธ์ new์ฐ์ฐ์๋ฅผ ํตํด ๊ฐ์ฒด ์์ฑ ๋ถ๊ฐ๋ฅํ๊ธฐ ๋๋ฌธ์ getInstance() ๋ฉ์๋๋ฅผ ํตํด์ ๊ฐ์ฒด ์์ฑ

```JAVA
Calendar c = Calendar.getInstance(); // Calendar ๊ฐ์ฒด ์์ฑ
```

- get(int field):int -> ์๋ ฅํ field(ex) Calendar.YEAR(๋๋))์ ๊ฐ ๋ฐํ

```JAVA
System.out.println(c.get(Calendar.YEAR)); // ํ์ฌ ๋๋ ๋ฐํ

System.out.println(c.get(Calendar.MONTH)); // ํ์ฌ ์ ๋ฐํ

System.out.println(c.get(Calendar.DATE)); // ํ์ฌ ์ผ ๋ฐํ

System.out.println(c.get(Calendar.AM_PM)); // ์ค์ ์ด๋ฉด 0 ์คํ๋ฉด 1 ๋ฐํ

System.out.println(c.get(Calendar.HOUR)); // ํ์ฌ  ์๊ฐ ๋ฐํ(12์๊ฐ ๊ธฐ์ค)

System.out.println(c.get(Calendar.HOUR_OF_DAY)); //  ํ์ฌ  ์๊ฐ ๋ฐํ (24์๊ฐ ๊ธฐ์ค)

System.out.println(c.get(Calendar.AM_PM)); // ์ค์ ์ด๋ฉด 0 ์คํ๋ฉด 1 ๋ฐํ

System.out.println(c.get(Calendar.MINUTE)); // ํ์ฌ ๋ถ ๋ฐํ

System.out.println(c.get(Calendar.SECOND)); // ํ์ฌ ์ด ๋ฐํ

System.out.println(c.get(Calendar.DAY_OF_WEEK)); //  ์์ผ ๋ฐํ (์ผ = 1 ..... ํ  =7)
```

---

## โ๏ธ GregorianCalendar ํด๋์ค

- GregorianCalendarโ(int year, int month, int dayOfMonth, int hourOfDay, int minute, int second) -> ๋, ์, ์ผ, ์, ๋ถ, ์ด๋ฅผ ์๋ ฅ๋ฐ๋ ์์ฑ์

```JAVA
GregorianCalendar gc = new GregorianCalendar(2022, 0, 1, 1, 1, 1);

System.out.println(gc.get(Calendar.YEAR)); // 2022 ์ถ๋ ฅ
System.out.println(gc.get(Calendar.MONTH)); // 1 ์ถ๋ ฅ (0์ธ๋ฑ์ค๋ถํฐ ์์ํ๊ธฐ ๋๋ฌธ์ ์๋ ฅํ ๋ -1ํด์ค์ผ ํจ)
System.out.println(gc.get(Calendar.DAY)); // 1 ์ถ๋ ฅ
```

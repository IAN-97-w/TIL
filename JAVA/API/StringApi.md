# ๐ป String Api

## โ๏ธ API๋?

    API(Application Programming interface)๋ ์์ฉ ํ๋ก๊ทธ๋จ์์ ์ฌ์ฉํ  ์ ์๋๋ก,  
    ์ด์ ์ฒด์ ๋ ํ๋ก๊ทธ๋๋ฐ ์ธ์ด๊ฐ ์ ๊ณตํ๋ ๊ธฐ๋ฅ์ ์ ์ดํ  ์ ์๊ฒ ๋ง๋  ์ธํฐํ์ด์ค๋ฅผ ๋ปํ๋ค.

## โ๏ธ String ๊ด๋ จ ํด๋์ค

- String ํด๋์ค
  > ๋ฌธ์์ด ๊ฐ ์์  ๋ถ๊ฐ๋ฅ, immutable(๋ถ๋ณ)  
  >  ์์ ์ ์์ ๋ ๋ฌธ์์ด์ด ์๋ก ํ ๋น ๋์ด ์ ์ฃผ์๋ฅผ ๋๊น
- StringBuffer ํด๋์ค
  > ๋ฌธ์์ด ๊ฐ ์์  ๊ฐ๋ฅ, mutable(๊ฐ๋ณ)  
  >  ์์ , ์ญ์  ๋ฑ์ด ๊ธฐ์กด ๋ฌธ์์ด์ ์์ ๋์ด ์ ์ฉ  
  >  ๊ธฐ๋ณธ 16๋ฌธ์ ํฌ๊ธฐ๋ก ์ง์ ๋ ๋ฒํผ๋ฅผ ์ด์ฉํ๋ฉฐ ํฌ๊ธฐ ์ฆ๊ฐ ๊ฐ๋ฅ  
  >  ์ฐ๋ ๋ safe๊ธฐ๋ฅ ์ ๊ณต(์ฑ๋ฅ ์ ํ ์์ธ)
- StringBuilder ํด๋์ค
  > StringBuffer์ ๋์ผํ๋ ์ฐ๋ ๋ safe๊ธฐ๋ฅ์ ์ ๊ณตํ์ง ์์

String์ ๋ถ๋ณ์ฑ์ ๊ฐ์ก๊ธฐ ๋๋ฌธ์ .concatํน์ +๋ฅผ ์ด์ฉํ ๊ฐ๋ณ๊ฒฝ์ ๊ธฐ์กด String์ ๋ค์ด์๋ ๊ฐ์ ๋ฒ๋ฆฌ๊ณ  ์๋ก์ด ๊ฐ์ ํ ๋นํ๋ ๊ฒ์ด๋ค.  
๋ฐ๋ผ์ .concatํน์ +๋ฅผ ๋ง์ด์ฌ์ฉํ๋ ๊ฒฝ์ฐ ์๋๊ฐ ๋๋ ค์ ธ ๋นํจ์จ์ ์ด๋ค.  
StringBuffer๋ StringBuilder๋ ๊ฐ์ ๋ณ๊ฒฝํ ์ ์๊ธฐ ๋๋ฌธ์ ๋ฌธ์์ด ์ฐ์ฐ(์ถ๊ฐ, ์์ )์ด ๋น๋ฒํ๋ค๋ฉด StringBuffer/StringBuilder๋ฅผ ์ฌ์ฉํ๋ฉด ๋๋ค.'

---

## โ๏ธ String ํด๋์ค

- concat(Strig str):String -> ๋ฌธ์์ด ๋ค์ ๋ฌธ์์ด ์ถ๊ฐ

```JAVA
String str = "JAVA"
String concatStr = str.concat("!!!");
System.out.println(concatStr);  // JAVA!!!์ถ๋ ฅ
```

- substring(int beginIndex):String -> beginIndex์์น ๋ถํฐ ๋๊น์ง ๋ฌธ์์ด ๋ฐํ

```JAVA
String str = "ABCDEFGHIJ";
System.out.println(str.substring(6)); // GHIJ ์ถ๋ ฅ
```

- substring(int beginIndex, int endIndex):String -> beginIndex ์์น ๋ถํฐ endIndex ์  ์์น๊น์ง ๋ฌธ์์ด ๋ฐํ

```JAVA
String str = "ABCDEFGHIJ";
System.out.println(str.substring(3, 7)); // DEFG ์ถ๋ ฅ
```

- replace(char oldChar, char newChar):String -> ๋ฌธ์์ด์ ์๋ ๋ชจ๋  oldChar๋ฅผ newChar๋ก ๋ณํ

```JAVA
String str = "AOBOCODOEOF";
System.out.println(str.replace('O', 'I')); // AIBICIDIEIF ์ถ๋ ฅ
```

- equalsIgnoreCase(String anotherString):bolean -> ๋ฌธ์์ด๊ณผ anotherString ๋์๋ฌธ์ ๊ด๊ณ์์ด ๋น๊ต

```JAVA
String str = "ABCDEFGH";
System.out.println(str.equalsIgnoreCase("abcdefgh")); // true ์ถ๋ ฅ
```

- trim():String -> ๋ฌธ์์ด์ ์๋ค ๋ชจ๋  ๊ณต๋ฐฑ ์ ๊ฑฐ

```JAVA
String str = "   AB C  E       ";
System.out.println(str.trim()); // AB C  E ์ถ๋ ฅ
```

- split(String regex):String[] -> ๋ฌธ์์ด์ ์๋ regex๋ฅผ ๊ธฐ์ค์ผ๋ก ๋ฌธ์์ด์ ์๋ผ String ๋ฐฐ์ด๋ก ๋ฐํ

```JAVA
String str = "A,B,C,D,E,F";
String[] Arr = str.split(",");
System.out.println(Arr[0]); //  A ์ถ๋ ฅ
System.out.println(Arr[1]); //  B ์ถ๋ ฅ
System.out.println(Arr[2]); //  C ์ถ๋ ฅ
System.out.println(Arr[3]); //  D ์ถ๋ ฅ
System.out.println(Arr[4]); //  E ์ถ๋ ฅ
System.out.println(Arr[5]); //  F ์ถ๋ ฅ
```

---

## โ๏ธ StringBuffer ํด๋์ค

- StringBuffer.append(String str):StringBuffer -> ๋ฌธ์์ด ๋ค์ ๋ฌธ์์ด ์ถ๊ฐ

```JAVA
StringBuffer buffer = new StringBuffer("JAVA");
System.out.println(buffer.append("!!!"));  // JAVA!!!์ถ๋ ฅ
```

- StringBuffer.insert(int offset, String str):StringBuffer -> ๋ฌธ์์ด์ offset๋ฒ์งธ ์ธ๋ฑ์ค์ str ์ฝ์

```JAVA
StringBuffer buffer = new StringBuffer("JAVA");
System.out.println(buffer.insert(2, "ooo"));  // JAoooVA์ถ๋ ฅ
```

- StringBuffer.delete(int start, int end):StringBuffer -> ๋ฌธ์์ด์ start๋ฒ์งธ ์ธ๋ฑ์ค๋ถํฐ end๋ฒ์งธ ์  ์ธ๋ฑ์ค๊น์ง ์ญ์ 

```JAVA
StringBuffer buffer = new StringBuffer("JAVA");
System.out.println(buffer.delete(2, 4));  // JA์ถ๋ ฅ
```

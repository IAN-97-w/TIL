# 💻 자바스크립트 기본 문법

## ✏️ 변수

### 변수 선언

- 변수명 = 값; : 전역 변수 (전역 변수 사용 시 'window.변수명' 혹은 'this.변수명'으로 표현하여 지역변수와 구분)
- var 변수명 = 값 : 지역 변수 (함수 밖에서 선언할 경우 전역 변수)

`전역 변수는 해당 window내 어디든 사용할 수 있으며, 지역 변수는 해당 함수 내에서만 사용 가능`

---

## ✏️ 자료형

자바스크립트에서는 자료형 별로 변수 타입이 지정되지 않고 리터럴에 의해 자료형 결정

- string : "",''로 묶여있는 리터럴

<img src="https://user-images.githubusercontent.com/105089699/191670712-cc115759-5589-4028-add5-35f453c6ec60.png" width="400px" height="200px">

- number : 정수형 숫자와 부동소수점 숫자로 구분

<img src="https://user-images.githubusercontent.com/105089699/191670885-decf272e-da91-497a-9b51-5d84915ec641.png" width="400px" height="200px">

- boolean : 논리 값, true, false 두 가지 값을 가짐
- Object : 객체, new로 선언된 사용자 객체와 자바스크립트 내장 객체
- undefined : 변수 명이나 함수 명으로 선언되지 않은 식별자일 때 지정
- function : 함수를 가지는 자료형

### typeof()

값의 자료형을 확인하는 연산자  
`선언 시 자료형을 지정하지 않아 변수 명을 보고 데이터 확인 불가 자료형 확인 시 자주 사용`

typeof("문자열값") -> string  
typeof(숫자) -> number  
typeof(참/거진) -> boolean  
typeof(객체) -> object  
typeof(초기값이 없는 변수) -> undefined  
typeof(function) -> function

## ✏️ 데이터 형변환

### ✓ 숫자 -> 문자열

숫자와 문자를 +연산하게 되면 문자가 우선되어 숫자를 문자로 변환  
강제 형변환 : String()함수 이용

### ✓ 문자열 -> 숫자

숫자,문자 + 이외의 사칙 연산 시 숫자가 우선돼 문자를 숫자로 변환  
강제 형변환 : Number(), parseInt(), parseFloat()함수 이용

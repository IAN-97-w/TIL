# 💻 이벤트

### 이벤트 활용

이벤트 속성과 이벤트 핸들러(함수)를 연동하여  
이벤트 발생 시 특정 기능을 하도록 하는 것

## ✏️ 이벤트 설정 방법

### 고전 이벤트 모델

요소 객체가 갖고 있는 이벤트 속성에 이벤트 핸들러를 연결하는 방법으로  
이벤트 객체를 제거할 땐 속성 값에 null을 넣어주면 됨  
이벤트 발생 객체는 핸들러 내부에서 this로 표현 가능(스타일 변경 가능)  
매개 변수로 이벤트 정보 전달(e, window.event) `이벤트 객체 전달 `

```JavaScript
<button id명>버튼</button>

const h = document.getElementById('id명');

h.onclick = function() {
    수행 기능 설정;
    h(this).onclick = null; // 한 번만 싷행
}
```

## ✏️ 인라인 이벤트 모델

요소 내부에 이벤트를 작성하는 방식으로  
인라인 방식은 \<script>태그에 있는 함수를 호출하는 방식 선호

```JavaScript
<h1 onclick='처리로직'></h1>
or
<h1 onclick='스크립트 내 함수 호출'></h1>
```

## ✏️ 표준 이벤트 모델

W3C에서 공식적으로 지정한 이벤트 모델  
한 번에 여러 개 이벤트 핸들러 설정 가능  
this키워드가 이벤트 발생 객체를 의미함

```JavaScript
const h = document.getElementById('id명');

h.addEventListener(이벤트이름, 핸들러); // 이벤트 설정
h.removeEventListener(이벤트이름, 핸들러); // 이벤트 삭제
```

## ✏️ 기본 이벤트 제거

기본 이벤트 : 태그 중 이벤트 핸들러를 기본적으로 가지고 있는 것  
`\<a>, \<input type="submit">입력 양식에서 많이 사용`  
유효성 검사 : 사용자가 입력한 데이터가 양식에 맞는지 검사  
`ex) 비밀번호 확인`

### 기본 이벤트 제거

onsubmit이벤트 속성에 이벤트 핸들러 연결할 때 return false;함

### 유효성 검사

이벤트 핸들러에 데이터 비교 후 맞지 않으면 false 리턴

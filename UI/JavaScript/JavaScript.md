# 💻 JavaScript

### 스크립트 언어

기본 프로그램의 동작을 사용자의 요구에 맞게 수행되도록 해주는 용도로 사용  
매우 빠르게 배우고 짧은 소스코드 파일로 상호작용 하도록 고안됨

### 클라이언트 사이드 스크립트

클라이언트, 즉 사용자 컴퓨터에서 처리되는 스크립트  
ex) JacaScript, VBscript, Jscript

### 서버 사이드 스크립트

정보를 제공하는 서버 쪽 컴퓨터에서 처리되는 스크립트  
ex) ASP, PHP, JSP, Perl, 파이썬, Node.js

### JavaScript

자바스크립트는 웹 브라우저에서 많이 사용하는 인터프리터 방식의 객체 지향 프로그래밍 언어로  
ECMA(European Computer Manufacturers Association) 스크립트 표준을 따르는 대표적인 웹 기술  
`인터프리터 방식 : 코드를 한 줄씩 읽어나가며 실행하는 방식`

---

## ✏️ 자바스크립트 작성 및 실행

### 자바스크립트 작성 방식

- inline 방식  
   자바스크립트 양이 한 두 줄 정도로 소량일 때 사용  
   html 태그의 on이벤트 속성을 이용하여 내장 메소드를 호출하거나 개발자가 선언한 사용자 정의 함수를 호출할 때 사용

  <태그 명 on이벤트 = "함수명();">

```JavaScript
<button onclick="alert('태그에 직접 자바스크립트 소스 작성');">클릭하세요!</button>
```

- inernal 방식  
   가장 일반적인 방식  
   자바스크립트 코드 작성, 함수 단위로 소스코드를 작성하고 html태그에서 이벤트 핸들러를 통해 함수를 실행시키는 방식

  \<script>실행할 소스코드 작성\</script>

```JavaScript
<button onclick="internal();">클릭해세요!</button>
	<script>
		function internal() {
			alert('script태그 안에 있는 internal()함수 실행');
		}
	</script>
```

- external 방식  
   자바스크립트 양이 많을 경우 자바스크립트 코드 부분을 외부 파일로 저장하여 작성  
   외부에 별도의 자바스크립트 소스파일(\*.js)을 작성하고 html에서 \<script src="경로.js">태그를 이용하여 해당 파일을 불러와 사용하는 방식

```JavaScript
<head>
    <script src="../js/sample.js"></script>
</head>
<body>
    <button onclick="external();">클릭하세요!</button>
</body>
```

### 자바스크립트 실행 방식

인터프리터 방식은 웹 브라우저에 내장되어 있는 자바스크립트 파서가 소스코드를 한 줄씩 읽고 해석함  
전체를 해석해 놓은 컴파일 언어와는 차이가 있음  
자바스크립트 실행은 작성된 html문서를 브라우저에서 읽으면 바로 실행을 할 수 있음

---

## ✏️ 데이터 입/출력

### 데이터 출력

- widow.alert(내용); : 내용을 메세지 창에 출력 (window객체는 모두 적용되는 것으로 생략 가능)

```Javascript
<script>
    alert('알림을 출력');
</script>
```

- document.write(내용); : 브라우저 화면 상의 페이지에 값 출력

```Javascript
<script>
	document.write('화면에 데이터 출력');
</script>
```

- innerHTML = 내용; : 태그 엘리먼트의 내용을 변경하여 출력

```Javascript
<p id="text">변경 전 내용</p>
<button onclick="testInnerHTML();">innerHTML</button>

<script>
    function testInnerHTML() {
        let text = document.getElementById('text');
        text.innerHTML = '변경 후 내용';
    }
</script>
```

- console.log(내용); : 개발자 도구 화면의 콘솔에 출력 (디버깅시 주로 사용)

```Javascript
<script>
    console.log('콘솔화면에 출력합니다.');
</script>
```

### 데이터 입력

- window.confirm() : 어떤 질문에 대해 "예/아니오"의 결과를 얻을 때 사용 `리턴 값 : true(확인)/false(취소)`

var 변수 = [window.]confirm("질문내용");

```Javascript
<script>
    var confirm = confirm('확인/취소');
</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191661067-a72e9260-a348-4abc-ba9a-2073daccfa32.png" width="300px" height="100px">

- window.prompt() : 텍스트 필드와 확인/취소버튼이 있는 대화 창 출력 `리턴 값 : 입력한 내용`

var 변수 = [window.]prompt('메세지');

```Javascript
<script>
    var prompt = prompt("텍스트 입력");
</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191662652-80aa57e1-dbc0-4b12-af10-fa3d35ba1a27.png" width="300px" height="100px">

---

## ✏️ HTML 태그 접근

- getElementById("아이디명"); : 태그의 id속성 값을 이용해 태그 엘리먼트 객체의 정보를 가져 옴 `리턴 값 : 단일 값(id는 중복 허용 안 함)`

```Javascript
<div id="area1" class="area"></div>
	<br>
	<button onclick="accessId();">아이디로 접근</button>
	<script>
		function accessId() {
			var area = document.getElementById('area1');
			area.style.backgroundColor = 'skyblue';
			area.innerHTML += '아이디로 접근 성공!<br>'; // innerHTML : HTML명령어를 해석해줌
		  //area.innerText += '아이디로 접근 성공!<br>'; // innerTEXT : HTML명령어를 해석할 수 없다
		}
	</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191663556-90e9b550-6b57-431a-8932-e51fa89d398c.png" width="300px" height="200px">

- getElementByName("이름"); : 태그의 name속성 값을 이용해 태그 엘리먼트의 객체 정보를 배열에 담아 가져 옴 `리턴 값 : 배열(name은 중복 가능)`

```Javascript
<form>
    <fieldset>
		<legend>취미</legend>
		<table>
			<tr>
				<td>
					<input type="checkbox" name="hobby" value="game" id="game">
					<label for="game">게임</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="music" id="music">
					<label for="music">음악감상</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="movie" id="movie">
					<label for="movie">영화보기</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="book" id="book">
					<label for="book">독서</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="travel" id="travel">
					<label for="travel">여행</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="exercise" id="exercies">
					<label for="movie">운동</label>
				</td>
			</tr>
		</table>
	</fieldset>
</form>
<br>
<div id="area2" class="area"></div><br>
<button onclick="accessName();">name으로 접근</button>
<script>
	function accessName(){
		var hobby = document.getElementsByName('hobby'); // 체크박스에 체크되어있으면 checked = true 아니면 false
		var checkItem = '';
		for(var i = 0; i < hobby.length; i++){
			if(hobby[i].checked){
				checkItem += hobby[i].value + ' 선택함<br>';
			}
		}

		document.getElementById('area2').innerHTML = checkItem;
	}
</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191665320-7dc63277-205a-4ee0-8a59-a70707d155ed.png" width="400px" height="200px">

- getElementsTagName("태그명") : 태그 명을 이용하여 해당 태그들의 객체 정보를 배열에 담아 가져옴 `리턴 값 : 배열(태그 중복 가능)`

```Javascript
<ul>
	<li>목록1</li>
	<li>목록2</li>
	<li>목록3</li>
	<li>목록4</li>
	<li>목록5</li>
</ul>
<button onclick="accessTagName();">태그 명으로 접근</button>
<script>
	function accessTagName(){
		var list = document.getElementsByTagName('li'); // 한 페이지에 같은 태그명이 여러개일 수 있기 때문에 Elements시용
		console.log(list);
		console.log(list[1]);
		var changeColor = 50;
		for(var i = 0; i < list.length; i++){
			list[i].style.backgroundColor = 'rgb(130, 220, ' + changeColor + ')';
			changeColor += 50;
		}
	}
</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191665879-750f6fbf-3bdd-40ed-8b28-51d162e4dd07.png" width="400px" height="200px">

# ๐ป JavaScript

### ์คํฌ๋ฆฝํธ ์ธ์ด

๊ธฐ๋ณธ ํ๋ก๊ทธ๋จ์ ๋์์ ์ฌ์ฉ์์ ์๊ตฌ์ ๋ง๊ฒ ์ํ๋๋๋ก ํด์ฃผ๋ ์ฉ๋๋ก ์ฌ์ฉ  
๋งค์ฐ ๋น ๋ฅด๊ฒ ๋ฐฐ์ฐ๊ณ  ์งง์ ์์ค์ฝ๋ ํ์ผ๋ก ์ํธ์์ฉ ํ๋๋ก ๊ณ ์๋จ

### ํด๋ผ์ด์ธํธ ์ฌ์ด๋ ์คํฌ๋ฆฝํธ

ํด๋ผ์ด์ธํธ, ์ฆ ์ฌ์ฉ์ ์ปดํจํฐ์์ ์ฒ๋ฆฌ๋๋ ์คํฌ๋ฆฝํธ  
ex) JacaScript, VBscript, Jscript

### ์๋ฒ ์ฌ์ด๋ ์คํฌ๋ฆฝํธ

์ ๋ณด๋ฅผ ์ ๊ณตํ๋ ์๋ฒ ์ชฝ ์ปดํจํฐ์์ ์ฒ๋ฆฌ๋๋ ์คํฌ๋ฆฝํธ  
ex) ASP, PHP, JSP, Perl, ํ์ด์ฌ, Node.js

### JavaScript

์๋ฐ์คํฌ๋ฆฝํธ๋ ์น ๋ธ๋ผ์ฐ์ ์์ ๋ง์ด ์ฌ์ฉํ๋ ์ธํฐํ๋ฆฌํฐ ๋ฐฉ์์ ๊ฐ์ฒด ์งํฅ ํ๋ก๊ทธ๋๋ฐ ์ธ์ด๋ก  
ECMA(European Computer Manufacturers Association) ์คํฌ๋ฆฝํธ ํ์ค์ ๋ฐ๋ฅด๋ ๋ํ์ ์ธ ์น ๊ธฐ์   
`์ธํฐํ๋ฆฌํฐ ๋ฐฉ์ : ์ฝ๋๋ฅผ ํ ์ค์ฉ ์ฝ์ด๋๊ฐ๋ฉฐ ์คํํ๋ ๋ฐฉ์`

---

## โ๏ธ ์๋ฐ์คํฌ๋ฆฝํธ ์์ฑ ๋ฐ ์คํ

### ์๋ฐ์คํฌ๋ฆฝํธ ์์ฑ ๋ฐฉ์

- inline ๋ฐฉ์  
   ์๋ฐ์คํฌ๋ฆฝํธ ์์ด ํ ๋ ์ค ์ ๋๋ก ์๋์ผ ๋ ์ฌ์ฉ  
   html ํ๊ทธ์ on์ด๋ฒคํธ ์์ฑ์ ์ด์ฉํ์ฌ ๋ด์ฅ ๋ฉ์๋๋ฅผ ํธ์ถํ๊ฑฐ๋ ๊ฐ๋ฐ์๊ฐ ์ ์ธํ ์ฌ์ฉ์ ์ ์ ํจ์๋ฅผ ํธ์ถํ  ๋ ์ฌ์ฉ

  <ํ๊ทธ ๋ช on์ด๋ฒคํธ = "ํจ์๋ช();">

```JavaScript
<button onclick="alert('ํ๊ทธ์ ์ง์  ์๋ฐ์คํฌ๋ฆฝํธ ์์ค ์์ฑ');">ํด๋ฆญํ์ธ์!</button>
```

- inernal ๋ฐฉ์  
   ๊ฐ์ฅ ์ผ๋ฐ์ ์ธ ๋ฐฉ์  
   ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋ ์์ฑ, ํจ์ ๋จ์๋ก ์์ค์ฝ๋๋ฅผ ์์ฑํ๊ณ  htmlํ๊ทธ์์ ์ด๋ฒคํธ ํธ๋ค๋ฌ๋ฅผ ํตํด ํจ์๋ฅผ ์คํ์ํค๋ ๋ฐฉ์

  \<script>์คํํ  ์์ค์ฝ๋ ์์ฑ\</script>

```JavaScript
<button onclick="internal();">ํด๋ฆญํด์ธ์!</button>
	<script>
		function internal() {
			alert('scriptํ๊ทธ ์์ ์๋ internal()ํจ์ ์คํ');
		}
	</script>
```

- external ๋ฐฉ์  
   ์๋ฐ์คํฌ๋ฆฝํธ ์์ด ๋ง์ ๊ฒฝ์ฐ ์๋ฐ์คํฌ๋ฆฝํธ ์ฝ๋ ๋ถ๋ถ์ ์ธ๋ถ ํ์ผ๋ก ์ ์ฅํ์ฌ ์์ฑ  
   ์ธ๋ถ์ ๋ณ๋์ ์๋ฐ์คํฌ๋ฆฝํธ ์์คํ์ผ(\*.js)์ ์์ฑํ๊ณ  html์์ \<script src="๊ฒฝ๋ก.js">ํ๊ทธ๋ฅผ ์ด์ฉํ์ฌ ํด๋น ํ์ผ์ ๋ถ๋ฌ์ ์ฌ์ฉํ๋ ๋ฐฉ์

```JavaScript
<head>
    <script src="../js/sample.js"></script>
</head>
<body>
    <button onclick="external();">ํด๋ฆญํ์ธ์!</button>
</body>
```

### ์๋ฐ์คํฌ๋ฆฝํธ ์คํ ๋ฐฉ์

์ธํฐํ๋ฆฌํฐ ๋ฐฉ์์ ์น ๋ธ๋ผ์ฐ์ ์ ๋ด์ฅ๋์ด ์๋ ์๋ฐ์คํฌ๋ฆฝํธ ํ์๊ฐ ์์ค์ฝ๋๋ฅผ ํ ์ค์ฉ ์ฝ๊ณ  ํด์ํจ  
์ ์ฒด๋ฅผ ํด์ํด ๋์ ์ปดํ์ผ ์ธ์ด์๋ ์ฐจ์ด๊ฐ ์์  
์๋ฐ์คํฌ๋ฆฝํธ ์คํ์ ์์ฑ๋ html๋ฌธ์๋ฅผ ๋ธ๋ผ์ฐ์ ์์ ์ฝ์ผ๋ฉด ๋ฐ๋ก ์คํ์ ํ  ์ ์์

---

## โ๏ธ ๋ฐ์ดํฐ ์/์ถ๋ ฅ

### ๋ฐ์ดํฐ ์ถ๋ ฅ

- widow.alert(๋ด์ฉ); : ๋ด์ฉ์ ๋ฉ์ธ์ง ์ฐฝ์ ์ถ๋ ฅ (window๊ฐ์ฒด๋ ๋ชจ๋ ์ ์ฉ๋๋ ๊ฒ์ผ๋ก ์๋ต ๊ฐ๋ฅ)

```Javascript
<script>
    alert('์๋ฆผ์ ์ถ๋ ฅ');
</script>
```

- document.write(๋ด์ฉ); : ๋ธ๋ผ์ฐ์  ํ๋ฉด ์์ ํ์ด์ง์ ๊ฐ ์ถ๋ ฅ

```Javascript
<script>
	document.write('ํ๋ฉด์ ๋ฐ์ดํฐ ์ถ๋ ฅ');
</script>
```

- innerHTML = ๋ด์ฉ; : ํ๊ทธ ์๋ฆฌ๋จผํธ์ ๋ด์ฉ์ ๋ณ๊ฒฝํ์ฌ ์ถ๋ ฅ

```Javascript
<p id="text">๋ณ๊ฒฝ ์  ๋ด์ฉ</p>
<button onclick="testInnerHTML();">innerHTML</button>

<script>
    function testInnerHTML() {
        let text = document.getElementById('text');
        text.innerHTML = '๋ณ๊ฒฝ ํ ๋ด์ฉ';
    }
</script>
```

- console.log(๋ด์ฉ); : ๊ฐ๋ฐ์ ๋๊ตฌ ํ๋ฉด์ ์ฝ์์ ์ถ๋ ฅ (๋๋ฒ๊น์ ์ฃผ๋ก ์ฌ์ฉ)

```Javascript
<script>
    console.log('์ฝ์ํ๋ฉด์ ์ถ๋ ฅํฉ๋๋ค.');
</script>
```

### ๋ฐ์ดํฐ ์๋ ฅ

- window.confirm() : ์ด๋ค ์ง๋ฌธ์ ๋ํด "์/์๋์ค"์ ๊ฒฐ๊ณผ๋ฅผ ์ป์ ๋ ์ฌ์ฉ `๋ฆฌํด ๊ฐ : true(ํ์ธ)/false(์ทจ์)`

var ๋ณ์ = [window.]confirm("์ง๋ฌธ๋ด์ฉ");

```Javascript
<script>
    var confirm = confirm('ํ์ธ/์ทจ์');
</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191661067-a72e9260-a348-4abc-ba9a-2073daccfa32.png" width="300px" height="100px">

- window.prompt() : ํ์คํธ ํ๋์ ํ์ธ/์ทจ์๋ฒํผ์ด ์๋ ๋ํ ์ฐฝ ์ถ๋ ฅ `๋ฆฌํด ๊ฐ : ์๋ ฅํ ๋ด์ฉ`

var ๋ณ์ = [window.]prompt('๋ฉ์ธ์ง');

```Javascript
<script>
    var prompt = prompt("ํ์คํธ ์๋ ฅ");
</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191662652-80aa57e1-dbc0-4b12-af10-fa3d35ba1a27.png" width="300px" height="100px">

---

## โ๏ธ HTML ํ๊ทธ ์ ๊ทผ

- getElementById("์์ด๋๋ช"); : ํ๊ทธ์ id์์ฑ ๊ฐ์ ์ด์ฉํด ํ๊ทธ ์๋ฆฌ๋จผํธ ๊ฐ์ฒด์ ์ ๋ณด๋ฅผ ๊ฐ์ ธ ์ด `๋ฆฌํด ๊ฐ : ๋จ์ผ ๊ฐ(id๋ ์ค๋ณต ํ์ฉ ์ ํจ)`

```Javascript
<div id="area1" class="area"></div>
	<br>
	<button onclick="accessId();">์์ด๋๋ก ์ ๊ทผ</button>
	<script>
		function accessId() {
			var area = document.getElementById('area1');
			area.style.backgroundColor = 'skyblue';
			area.innerHTML += '์์ด๋๋ก ์ ๊ทผ ์ฑ๊ณต!<br>'; // innerHTML : HTML๋ช๋ น์ด๋ฅผ ํด์ํด์ค
		  //area.innerText += '์์ด๋๋ก ์ ๊ทผ ์ฑ๊ณต!<br>'; // innerTEXT : HTML๋ช๋ น์ด๋ฅผ ํด์ํ  ์ ์๋ค
		}
	</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191663556-90e9b550-6b57-431a-8932-e51fa89d398c.png" width="300px" height="200px">

- getElementByName("์ด๋ฆ"); : ํ๊ทธ์ name์์ฑ ๊ฐ์ ์ด์ฉํด ํ๊ทธ ์๋ฆฌ๋จผํธ์ ๊ฐ์ฒด ์ ๋ณด๋ฅผ ๋ฐฐ์ด์ ๋ด์ ๊ฐ์ ธ ์ด `๋ฆฌํด ๊ฐ : ๋ฐฐ์ด(name์ ์ค๋ณต ๊ฐ๋ฅ)`

```Javascript
<form>
    <fieldset>
		<legend>์ทจ๋ฏธ</legend>
		<table>
			<tr>
				<td>
					<input type="checkbox" name="hobby" value="game" id="game">
					<label for="game">๊ฒ์</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="music" id="music">
					<label for="music">์์๊ฐ์</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="movie" id="movie">
					<label for="movie">์ํ๋ณด๊ธฐ</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="book" id="book">
					<label for="book">๋์</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="travel" id="travel">
					<label for="travel">์ฌํ</label>
				</td>
				<td>
					<input type="checkbox" name="hobby" value="exercise" id="exercies">
					<label for="movie">์ด๋</label>
				</td>
			</tr>
		</table>
	</fieldset>
</form>
<br>
<div id="area2" class="area"></div><br>
<button onclick="accessName();">name์ผ๋ก ์ ๊ทผ</button>
<script>
	function accessName(){
		var hobby = document.getElementsByName('hobby'); // ์ฒดํฌ๋ฐ์ค์ ์ฒดํฌ๋์ด์์ผ๋ฉด checked = true ์๋๋ฉด false
		var checkItem = '';
		for(var i = 0; i < hobby.length; i++){
			if(hobby[i].checked){
				checkItem += hobby[i].value + ' ์ ํํจ<br>';
			}
		}

		document.getElementById('area2').innerHTML = checkItem;
	}
</script>
```

<img src="https://user-images.githubusercontent.com/105089699/191665320-7dc63277-205a-4ee0-8a59-a70707d155ed.png" width="400px" height="200px">

- getElementsTagName("ํ๊ทธ๋ช") : ํ๊ทธ ๋ช์ ์ด์ฉํ์ฌ ํด๋น ํ๊ทธ๋ค์ ๊ฐ์ฒด ์ ๋ณด๋ฅผ ๋ฐฐ์ด์ ๋ด์ ๊ฐ์ ธ์ด `๋ฆฌํด ๊ฐ : ๋ฐฐ์ด(ํ๊ทธ ์ค๋ณต ๊ฐ๋ฅ)`

```Javascript
<ul>
	<li>๋ชฉ๋ก1</li>
	<li>๋ชฉ๋ก2</li>
	<li>๋ชฉ๋ก3</li>
	<li>๋ชฉ๋ก4</li>
	<li>๋ชฉ๋ก5</li>
</ul>
<button onclick="accessTagName();">ํ๊ทธ ๋ช์ผ๋ก ์ ๊ทผ</button>
<script>
	function accessTagName(){
		var list = document.getElementsByTagName('li'); // ํ ํ์ด์ง์ ๊ฐ์ ํ๊ทธ๋ช์ด ์ฌ๋ฌ๊ฐ์ผ ์ ์๊ธฐ ๋๋ฌธ์ Elements์์ฉ
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

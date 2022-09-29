# 💻 Window 객체

<img src="https://user-images.githubusercontent.com/105089699/192839009-7532cf4a-e20b-48c5-9347-78ccdd22af45.png" width="400px">

브라우저 창에 대한 설정을 하는 객체로 자바스크립트에서의 최상위 객체, BOM과 DOM을 나뉨  
생성되는 모든 객체는 window객체 하위 존재

wondow.open('주소', '이름 또는 open방식', '형태');

## ✏️ 형태 옵션

| _height_  |  윈도우 높이  |     값     |
| :-------: | :-----------: | :--------: |
|   width   |  윈도우 너비  |     값     |
| location  | 주소 입력 창  | yes/no/1/0 |
|  menubar  |   메뉴유무    | yes/no/1/0 |
| resizeble | 화면크기 조절 | yes/no/1/0 |
|  status   |  상태표시줄   | yes/no/1/0 |
|  toolbar  |   툴바 표시   | yes/no/1/0 |

## ✏️ window객체의 timer메소드

### setTimeout(함수, 시간(ms))

일정시간 후 함수를 한번 실행/ id값 리턴

```JavaScript
window.setTimeout(function() { // 함수안에 있는 내용을 n초후에 실행
	실행할 내용;
}, 3000); // 3000 = 3초

```

### setInterval(함수, 시간(ms))

일정시간마다 함수를 반복 실행 / id값 리턴

```JavaScript
window.setInterval(function() { // 함수안에 있는 내용을 1초마다 반복
    실행할 내용;
}, 1000); // 1초 마다 반복
```

### clearInterval(id)

setInterval() 함수 종료

```JavaScript
const interval = window.setInterval(function() {
    실행할 내용;
}, 3000);

clear(interval); // interval 종료
```

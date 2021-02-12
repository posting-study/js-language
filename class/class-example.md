# Canvas를 활용한 객체지향 맛보기

### Canvas란?

웹 환경에서 그래픽을 표현하기 위한 API로
그림판에 그림을 그리듯이 그래픽을 랜더링하는 것이 특징입니다.

아래와 같이 HTML 코드를 작성하고
### 
```html
<!-- index.html -->
<html>
    <head>
        <script src='./index.js'>
    </head>
    <body>
        <canvas id="canvas"></canvas>
    </body>
</html>
```

브라우저가 로딩되면 캔버스 노드를 불러오는 코드를 작성해줍니다.
```js
/** index.js */
window.onload = () => {
    const canvas = document.getElementById('canvas');
    const ctx = canvas.getContext('2d');
}
```

캔버스에는 그래픽을 표현할 수 있는 다양한 속성들이 존재합니다.

아래와 같은 코드를 작성하게되면 (0, 0) 좌표에 가로 100, 새로 100 크기의 붉은 도형이 생성됩니다.
```js
/** index.js */
window.onload = () => {
    ...
    ctx.fillStyle = 'red';
    ctx.fillRect(0, 0, 100, 100);
    /** ctx.fillRect(x, y, width, height) */
}
```

### 


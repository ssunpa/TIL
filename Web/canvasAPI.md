# Canvas API

**Canvas API**는 그래픽을 그리기 위한 수단으로 제공한다.

주로 2D그래픽에 중점을 두고 있다.

## **Canvas Tutorial**

캔버스 크기의 초기 설정값은 300px _ 150px (너비 _ 높이)이다.

HTML `height`와 `width` 속성을 사용하여 바꿀 수 있다.

캔버스에 그림을 그리려면 자바스크립트 컨텍스트 오브젝트를 사용하며, 즉석에서 그림을 생성할 수 있다.

### `<Canvas>` 요소

```html
<canvas id="tutorial" width="150" height="150"></canvas>
```

`<canvas>`요소에는 `whidth`와 `height`의 두 속성만 존재한다. 요소는 CSS에 의해 임의로 크기를 정할 수 있지만 렌더링하는 동안 이미지는 레이아웃 크기에 맞게 크기가 조정된다.

> ☝ 만약 렌더링에서 왜곡된 것처럼 보이는 경우는 CSS를 사용하지 않고 `<canvas>` 속성에서 `width` 및 `height` 속성을 명시적으로 지정하는 것이 좋다.

`<canvas>`요소는 일반적인 이미지처럼 스타일을 적용시키는 것이 가능하다. 하지만 이 것은 실제 캔버스 위에 그리는 것에는 영향을 주지는 않다. 캔버스에 스타일링이 따로 지정되어있지 않다면 투명으로 설정되어 있다.

캔버스를 지원하지 않는 오래된 브라우저들을 위해서는 대체 컨텐츠를 제공한다.

```html
<canvas id="clock" width="150" height="150">
    <img src="images/clock.png" width="150" height="150" alt="" />
</canvas>
```

`<canvas>`태그 안에 대체 컨텐츠를 삽입한다면, `<canvas>`를 지원하지 않는 브라우저는 컨테이너를 무시하고 컨테이너 내부의 대체 콘텐츠를 렌더링 하고, 반대로 `<canvas>`를 지원하는 브라우저에서는 컨테이너 내부의 내용을 무시하고 캔버스를 정상적으로 렌더링한다.

> ☝ 이때문에 `<canvas>`는 닫는 태그가 꼭 필요하다!

### 렌더링 컨텍스트

`<canvas>` 엘리먼트는 고정 크기의 드로잉 영역을 생성하고 하나 이상의 렌더링 컨텍스트를 노출하여 출력할 컨텐츠를 생성하고 다룬다.

비어있는 캔버스에 `getContext()` 메서드를 이용해 랜더링 컨텍스트에 접근하여 무언가를 그릴 수 있다.

`getContext()` 메서드는 렌더링 컨텍스트 타입을 지정하는 하나의 파라메터를 갖는다.

```jsx
const canvas = document.getElementById('tutorial');
const ctx = canvas.getContext('2d');
```

`getContext()` 메소드의 존재 여부를 테스트함으로써 해당 브라우저에서의 지원여부를 검사할 수 있다.

```jsx
const canvas = document.getElementById('tutorial');

if (canvas.getContext) {
    const ctx = canvas.getContext('2d');
    // drawing code here
} else {
    // canvas-unsupported code here
}
```

---

## Drawing shapes with canvas

캔버스를 이용해 삼각형, 사각형, 선, 아치, 곡선 등 다양한 도형을 그릴수 있다.

캔버스 위에 물체를 그릴 때에는 path를 사용하는것이 필수이다.

### 그리드

기본적으로 그리드의 1단위는 캔버스의 1픽셀과 같다. 그리드의 원점은 좌측상단의 (0,0)이고 모든 요소들은 이 원점을 기준으로 위치된다.

### 직사각형 그리기

`<canvas>`는 오직 하나의 원시적인 도형만을 제공한다. 이에 직사각형이 포함된다. 다른 도형들은 무조건 하나 이상의 path와 여러 점으로 이어진 선으로 만들어진다.

캔버스에 직사각형을 바로 그리는 세가지 함수

-   `fillRect(x, y, width, height)`
    검정 직사각형을 그리는 함수
-   `strokeRect(x, y, width, height)`
    직사각형의 윤곽선을 그리는 함수
-   `clearRect(x, y, width, height)`
    특정 부분을 지우는 직사각형을 그리는 함수. 이 때 지워진 부분은 완전히 투명해진다.

세 함수는 모두 같은 변수를 가진다. `x`와 `y`는 캔버스의 원점으로부터 상대적인 사각형의 위치를 결정하며, `width`와 `height`는 사각형의 크기를 결정한다.

현재 열린 패스에 직사각형 경로(path)를 추가하는 경우

-   `rect(x, y, width, height)`
    좌측상단이 (`x`, `y`)이고 폭이 `width` 이고 높이가 `height`인 직사각형을 그린다.
    이 메소드가 실행되기 전에 (`x`, `y`) 매개변수를 가진 `moveTo()` 메소드가 자동으로 호출된다.
    > ☝ 현재의 펜위치가 자동으로 기본 좌표로 초기화 된다.

### 경로(path) 그리기

경로는 점들의 집합이며, 직사각형 이외의 유일한 원시적인 도형이다.

경로를 이용하여 도형을 그리는 방법

1. 경로를 생성한다.
2. 그리기 명령어를 사용해 경로상에 그린다.
3. 경로를 렌더링 하기 위해서 윤곽선을 그리거나 도형 내부를 채울 수 있다.

-   `beginPath()`
    새로운 경로를 만든다. 이후 그리기 명령들은 경로를 구성하고 만드는데 사용하게 된다.
-   `closePath()`
    현재 하위 경로의 시작 부분과 연결된 직선을 추가한다.
-   `stroke()`
    윤곽선을 이용해 도형을 그린다.
-   `fill()`
    경로의 내부를 채워서 내부가 채워진 도형을 그린다.

`beginPath()` 메소드를 사용해 하위 경로의 모음을 초기화하고 새로운 도형을 그릴 준비를 한다.

> ☝ 현재 열린 path가 비어있는 경우(`beginPath()` 메소드를 사용한 직후, 혹은 캔버스를 새로 생성한 직후)에는 첫 경로 생성 명령은 실제 동작에 상관없이 `moveTo()`로 여겨진다. 이 때문에 경로를 초기화한 직후에는 항상 명확하게 시작 위치를 설정하는 것이 좋다.

경로가 그려지는 위치를 설정하는 메소드를 호출한 후 선택사항으로 `closePath()` 메소드를 호출한다.

`closePath()` 메소드는 현재 점 위치와 시작점 위치를 직선으로 이어서 도형을 닫는다. 이미 도형이 닫혀있거나 한 점만 존재한다면, 이 메소드는 아무것도 하지 않는다.

> ☝ `fill()` 메소드 호출 시 `stroke()` 메소드와는 다르게 열린 도형은 자동으로 닫기 때문에 `closePath()`메소드를 호출하지 않아도 된다.

**삼각형을 그리는 예시**

```jsx
function draw() {
    const canvas = document.querySelector('#canvas');
    if (canvas.getContext) {
        const ctx = canvas.getContext('2d');

        ctx.beginPath();
        ctx.moveTo(70, 30);
        ctx.lineTo(30, 100);
        ctx.lineTo(110, 100);
        ctx.fill();
    }
}
```

`moveTo(x, y)` 함수는 펜을 `x`와 `y`로 지정된 좌표로 옮긴다.

실제로 어떤 것도 그리지 않지만 경로의 일부가 된다. 펜이나 연필을 종이위에서 들어서 옆으로 이동하는 것이라고 보면된다.

현재 열린 캔버스가 비어있는 경우 특정 시작점 설정을 위해 `moveTo(x, y)` 함수를 사용하는 것이 좋다. 또한 `moveTo(x, y)` 함수는 연결되지 않은 경로를 그리는데에도 사용가능하다.

`lineTo(x, y)` 함수는 현재의 드로잉 위치에서 `x`와 `y`로 지정된 좌표까지 선을 그린다.

이 함수의 시작점은 이전에 그려진 경로에 의해 결정 되며, 이전 경로의 끝점이 다음 경로의 시작점이 된다.

> ☝ 시작점을 변경하기 위해 `moveTo()` 메소드를 이용할 수 있다.

**웃는 얼굴을 그리는 예시**

```jsx
function draw() {
    const canvas = document.getElementById('canvas');
    if (canvas.getContext) {
        const ctx = canvas.getContext('2d');

        ctx.beginPath();
        ctx.arc(75, 75, 50, 0, Math.PI * 2, true); // 얼굴
        ctx.moveTo(110, 75);
        ctx.arc(75, 75, 35, 0, Math.PI, false); // 입
        ctx.moveTo(65, 65);
        ctx.arc(60, 65, 5, 0, Math.PI * 2, true); // 왼쪽 눈
        ctx.moveTo(95, 65);
        ctx.arc(90, 65, 5, 0, Math.PI * 2, true); // 오른쪽 눈
        ctx.stroke();
    }
}
```

`arc()`혹은 `arcTo()` 메소드는 원이나 호를 그릴 때 사용한다.

-   `arc(x, y, radius, startAngle, endAngle, anticlockwise)`
    (`x`, `y`) 위치에 원점을 두면서 반지름 `radius`를 가지고, `startAngle`에서 시작하여 `endAngle`에서 끝나며 주어진 `anticlockwise`방향으로 향하는(기본값은 시계방향 회전) 호를 그린다.
    `startAngle`과 `endAngle`은 x축을 기준으로 원의 커브를 따라 호의 시작점과 끝점을 라디안 단위로 정의한다.
    `anticlockwise` 는 Boolean값을 가지며 true일 때 호를 반시계 방향으로 그리게 된다.
-   `arcTo(x1, y1, x2, y2, radius)`
    주어진 제어점들(`x1, y1, x2, y2`)과 반지름 `radius`으로 호를 그리고, 이전 점과 직선으로 연결한다.

### 베지어(Bezier) 곡선과 이차(Quadratic) 곡선

이 타입은 복잡한 대게 복잡한 형태를 그리는데 사용된다.

-   `quadraticCurveTo(cp1x, cp1y, x, y)`
    `cp1x` 및 `cp1y`로 지정된 제어점을 사용하여 현재 펜의 위치에서 `x`와 `y`로 지정된 끝점까지 이차 베지어 곡선을 그린다.
-   `bezierCurveTo(cp1x, cp1y, cp2x, cp2y, x, y)`
    (`cp1x`, `cp1y`) 및 (`cp2x`, `cp2y`)로 지정된 제어점을 사용하여 현재 펜 위치에서 `x`와 `y`로 지정된 끝점까지 삼차 베지어 곡선을 그린다.

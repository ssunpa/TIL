# Hoisting

일반적으로 코드는 위에서 아래로 실행이 되지만 호이스팅 시 변수는 선언과 동시에 undefined로 초기화가 된다.

```jsx
console.log(hello); // undefined
var hello = 10;
console.log(hello); // 10
```

위 코드와 아래 코드는 동일한 결과물을 보여준다.

```jsx
var hello;
console.log(hello); // undefined
hello = 10;
console.log(hello); // 10
```

자바스크립트는 마치 선언부를 최상위로 올려준 것처럼 작동한다.

<aside>
💡 호이스팅은 추가적으로 만들어준 기능이 아니다. 오히려 아무것도 안해줘서 만들어진 기능이라 할 수 있다.

</aside>

## var와 let

```jsx
console.log(a); // OK!
var a = 10;

console.log(b); // ERROR! //Cannot access 'b' before initialization
let b = 10;
```

엄밀히 말하면 `const`와 `let`도 hoisting이 되지만 선언 전에 변수를 사용할 수 없도록 *추가 기능*을 구현

<aside>
💡 TDZ(Temporal Death Zone) → 변수 선언 전 접근을 금지

</aside>

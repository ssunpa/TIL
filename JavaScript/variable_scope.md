# Variable Scope

변수 유효 범위

## Scope

참조 대상 식별자를 찾아내기 위한 규칙이다. 자바스크립트는 식별자 이름의 충돌을 방지하기 위해 이 규칙대로 식별자를 찾는다.

-   Global Scope(전역 스코프)
    코드 어디에서든 참조 가능
-   Local Scope or Function-level Scope(지역 스코프)
    함수 자신과 하위 함수에서만 참조 가능

<aside>
💡 모든 변수는 선언 위치에 따라 스코프를 가진다.

</aside>

## Variable

-   Global Variable(전역 변수)
    전역에서 선언된 변수
-   Local Variable(지역 변수)

    지역(함수) 내에서 선언된 변수

-   전역 변수 사용을 자제해야 하는 이유?
    JS는 다른 언어와 달리 시작점이 없으며 코드가 나타나는 즉시 해석하고 실행하고, 이는 *전역 변수 남발의 문제*를 야기한다.
      <aside>
      💡 전역 변수 남발의 문제 → 변수 이름이 중복될 수도 있고, 의도치 않은 재할당에 의한 상태 변화로 코드를 예측하기 어렵게 만든다.
      
      </aside>

## var vs let

```jsx
var a = 10;
var a = 20; // OK!

let b = 10;
let b = 20; // ERROR! //'b' has already been declared
```

`var`는 function scope에서 동작하고 `let`은 block scope에서 동작

```jsx
//block scope
if(condition){
	...block scope...
}
switch(item){
	...block scope...
}
for(const item of items){
	...block scope...
}
while(condition){
	...block scope...
}
//funcion scope
function hello(){
	...function scope...
}
const world = () => {
	...function scope...
}
```

## var로 변수 선언 시

자바스크립트는 블록 레벨 스코프를 사용하지 않으므로 함수 밖에서 선언된 변수는 코드 블록 내에서 선언되었다 할지라도 모두 전역 스코프를 가진다.

```jsx
var a = 10;
if (true) {
    var a = 20;
    console.log(a); // 20
}
console.log(a); // 20
```

block scope는 무시

```jsx
var b = 10;
function test() {
    var b = 20;
    console.log(b); //20
}
test();
console.log(b); // 10
```

함수 내부와 외부가 독립적

<aside>
💡 block scope ⊂ function scope

</aside>

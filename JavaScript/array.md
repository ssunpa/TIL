# 배열 내장 함수

## forEach

배열 요소를 가지고 반복 작업을 수행해준다.

```jsx
arr.forEach(function (item, index, array) {
    //요소에 대해 반복 수행할 코드
});
```

콘솔창에 배열의 각 요소를 찍는 코드 예시

```jsx
const AAPL = ['iphone', 'ipad', 'mac'];

AAPL.forEach(function (arr) {
    console.log(arr);
});

//console창에 iphone, ipad, mac을 차례로 출력
```

인덱스 정보도 같이 출력 가능

```jsx
const AAPL = ['iphone', 'ipad', 'mac'];

AAPL.forEach(function (item, index, array) {
    console.log(`${item}'s index number is ${index} in [ ${array} ]`);
});

/*
iphone's index number is 0 in [ iphone,ipad,mac ] 
ipad's index number is 1 in [ iphone,ipad,mac ] 
mac's index number is 2 in [ iphone,ipad,mac ]
*/
```

---

## map

배열의 요소 전체를 대상으로 함수를 호출하고, 결과 값을 배열로 반환한다.

```jsx
arr.map(function (item, index, array) {
    // 각 원소를 가지고 새로운 배열을 반환.
});
```

각 원소를 가지고 새로운 배열을 만들 때 사용

```jsx
const array = [1, 2, 3, 4, 5, 6, 7];

const square = array.map(function (num) {
    return num * num;
});
console.log(square);

//[1, 4, 9, 16, 25, 36, 49]
```

---

## indexof

원하는 항목의 인덱스 번호를 반환

```jsx
const AAPL = ['iphone', 'ipad', 'mac'];

console.log(AAPL.indexOf('mac'));

//2
```

-   요소를 찾을 때 완전 항등 연산자 `===` 을 사용
-   반환 값이 `-1` 라면 값을 못 찾았다는 의미
-   배열과 객체는 찾을 수 없다.

---

## find 와 findIndex

객체로 구성되어 있는 배열의 요소를 찾는 방법

```jsx
const result = arr.find(function (item, index, array) {
    //첫 번째 true값을 반환
    //못 찾으면 undefined를 반환
});
```

-   `arr.find`는 함수가 참이 되면 반복이 멈추고 해당 요소 자체를 반환한다.
-   `arr.findIndex` 도 마찬가지지만 해당 요소의 인덱스 값을, 만약 못 찾으면 `-1`을 반환한다.

```jsx
const AAPL = [
    {
        id: 1,
        device: 'iphone',
        got: true,
    },
    {
        id: 2,
        device: 'ipad',
        got: true,
    },
    {
        id: 3,
        device: 'mac',
        got: false,
    },
];

const result_1 = AAPL.find((item) => item.id === 1);
const result_2 = AAPL.findIndex((item) => item.id === 1);

console.log(result_1); // {id: 1, device: "iphone", got: true}
console.log(result_2); // 0
```

---

## filter

배열에서 특정 조건을 만족하는 요소가 여러 개일 경우 새로운 배열로 담아서 반환한다.

```jsx
const results = arr.filter(function (item, index, array) {
    // 조건을 충족하는 요소를 results에 순차적으로 더한다.
    // 조건을 충족하는 요소가 하나도 없으면 빈 배열을 반환한다.
});
```

아래 예시를 보면,

```jsx
const AAPL = [
    {
        id: 1,
        device: 'iphone',
        got: true,
    },
    {
        id: 2,
        device: 'ipad',
        got: true,
    },
    {
        id: 3,
        device: 'imac',
        got: false,
    },
    {
        id: 4,
        device: 'macbook',
        got: false,
    },
    {
        id: 5,
        device: 'airpods',
        got: true,
    },
];

const got_it = AAPL.filter((item) => item.got === true);
const want_it = AAPL.filter((item) => item.got === false);
```

`console.log(got_it)`의 결과

```jsx
[Object, Object, Object]
0: {id: 1, device: "iphone", got: true}
1: {id: 2, device: "ipad", got: true}
2: {id: 5, device: "airpods", got: true}
```

`console.log(want_it)`의 결과

```jsx
[Object, Object]
0: {id: 3, device: "imac", got: false}
1: {id: 4, device: "macbook", got: false}
```

---

## splice

배열에서 특정 요소를 제거 가능

```jsx
const txt = ['I', 'want', 'to', 'buy', 'a MacBook'];

// 인덱스 1에서부터 총 2개를 지움
txt.splice(1, 2);

console.log(txt); // ["I", "buy", "a MacBook"]
```

다른 요소로 교체 가능!

```jsx
const txt = ['I', 'want', 'to', 'buy', 'a MacBook'];

txt.splice(1, 2, 'am', 'gonna');

console.log(txt); //["I", "am", "gonna", "buy", "a MacBook"]
```

`indexOf`랑 같이 사용할 수 있다.

```jsx
const txt = ['I', 'want', 'to', 'buy', 'a MacBook'];
const start = txt.indexOf('want');

txt.splice(start, 2, 'am', 'gonna');

console.log(txt); // ["I", "am", "gonna", "buy", "a MacBook"]
```

---

## slice

`arr.splice`와 다르게 기존 배열은 건들지 않는다.

```jsx
arr.slice([start], [end]);
//start 인덱스 부터 end 인덱스 바로 전까지의 요소를 복사해요.
```

인수를 하나도 넘기지 않고 호출하면 기존의 배열을 건드리지 않고 그대로 복제한다.

```jsx
const AAPL = ['iphone', 'ipad', 'mac', 'airpods'];

console.log(AAPL.slice(0, 2)); // ["iphone", "ipad"]
console.log(AAPL.slice()); // ["iphone", "ipad", "mac", "airpods"]
console.log(AAPL); // ["iphone", "ipad", "mac", "airpods"]
```

---

## pop 과 push

`pop` 은 배열 마지막의 요소를 추출하고, `push` 는 배열 마지막에 요소를 추가한다.

```jsx
const AAPL = ['iphone', 'ipad', 'mac', 'airpods'];
const del = AAPL.pop();

console.log(del); // airpods
console.log(AAPL); // ["iphone", "ipad", "mac"]
```

`pop`으로 추출한 요소는 기존 배열에서 삭제된다. 이어서 `push`를 한다면,

```jsx
AAPL.push('macbook'); // 여러 개를 한 번에 더해주기도 가능

console.log(AAPL); // ["iphone", "ipad", "mac", "macbook"]
```

---

## shift 와 unshift

`shift` 는 배열 맨 앞의 요소를 추출하고, `unshift` 는 배열 맨 앞에 요소를 추가한다.

```jsx
const AAPL = ['iphone', 'ipad', 'mac', 'airpods'];
const del = AAPL.shift();

console.log(del); // iphone
console.log(AAPL); // ["ipad", "mac", "airpods"]
```

기존의 배열에서 첫 번째 요소 삭제

```jsx
AAPL.unshift('macbook'); // 여러 개를 더하는 것도 가능

console.log(AAPL); // ["macbook", "ipad", "mac", "airpods"]
```

---

## concat

`arr.concat` 은 여러 개의 배열을 하나로 합쳐줄 때 사용

```jsx
arr.concat(arg1, arg2...);
```

인수엔 배열이나 값이 올 수 있는데, 무한으로 연결 가능

코드를 실행하면 `arr`에 `arg1`과 `arg2...` 에 있는 모든 요소를 몽땅 합친 하나의 새로운 배열을 반환

```jsx
const want_it = ['mac', 'macbook'];
const got_it = ['iphone', 'ipad'];

const AAPL = want_it.concat(got_it, 'airpods');

console.log(AAPL);

// ["mac", "macbook", "iphone", "ipad", "airpods"]
```

---

## join

`arr.join` 은 모든 요소를 합쳐서 문자열로 반환한다.

```jsx
const txt = ['I', 'want', 'to', 'buy', 'a MacBook'];

console.log(txt.join(' ')); // ' '공백 하나를 이용해 연결

// I want to buy a MacBook
```

---

## reduce

배열을 기반으로 한 개의 결과를 가져올 때 사용

```jsx
let value = arr.reduce(
    function (accumulator, current, index, array) {
        // ...
    },
    [initial]
);
```

-   `initial` : 함수 최초 호출될 때 사용 되는 초기 값. (옵션)
-   `accumulator` : 이전 함수 호출의 결과
-   `current` : 현재 요소
-   `index` : 현재 요소의 인덱스
-   `array` : 배열

```jsx
//배열의 모든 요소의 합을 구하는 코드
const numbers = [2, 4, 6, 8, 10];

let sum = numbers.reduce((accumulator, current) => accumulator + current, 0);

console.log(sum);

// 30
```

-   함수 최초 호출 시 `accumulator = 0(초기 값)` 이고, `current = 2` 이 됨.
-   두 번째 호출 시 `accumulator = 2` 가, `current = 4` 가,
-   세 번째 호출 시 `accumulator = 6` 이, `current = 6` 이,
-   네 번째 호출 시 `accumulator = 12` 가, `current = 8` 이,
-   마지막 호출 시 `accumulator = 20` 이, `current =10` 이 할당되어 최종 결과 값 `30`을 반환.

내부 값을 알아보기 위해 찍어보는 코드

```jsx
const numbers = [2, 4, 6, 8, 10];

let sum = numbers.reduce((accumulator, current, index) => {
    console.log({ accumulator, current, index });
    return accumulator + current;
}, 0);
```

의 결과

```jsx
{accumulator: 0, current: 2, index: 0}
{accumulator: 2, current: 4, index: 1}
{accumulator: 6, current: 6, index: 2}
{accumulator: 12, current: 8, index: 3}
{accumulator: 20, current: 10, index: 4}
```

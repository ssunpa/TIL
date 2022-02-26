# async & await

## async

원래는 `promise`에 대해서 `then`과 `catch`를 직접 다뤄야 함

```jsx
function test() {
    fetch('...url...')
        .then((response) => {
            //do something
        })
        .catch((error) => {
            //handle error
        });
}
```

함수 선언 `prefix` 에 `async` 키워드를 추가한다면 함수 블럭을 자동으로 `promise`로 변환함

```jsx
async function test() {
    try {
        const response = await fetch('...url...');
        //do something
    } catch (error) {
        //handle error
    }
}
```

`then` 대신 `await`을 사용하고 `catch` 처리는 `try... catch`문으로 대체

## await

-   `await`식은 `async`함수의 실행을 일시 중지하고 전달 된 `Promise`의 해결을 기다린 다음 `async`
     함수의 실행을 다시 시작하고 완료 후 값을 반환
-   `await` 키워드는 `async` 함수 내부에서만 유효

<aside>
💡 `async await`은 새로운 것이 아니라 `promise` 위 간편 API를 제공한 것이다.

</aside>

## Promise chaning과의 비교

`Promise`를 반환받아 이어붙이는 형식을 `Promise chaning`이라 함

```jsx
function test() {
    return doSomethingAsync()
        .then((hello) => doAsync2(hello))
        .then((world) => doAsync3(world))
        .then((foo) => doAsync4(foo))
        .then((bar) => doAsync5(bar));
}
```

사실 변수의 생명 주기는 chaning이 더 짧다.

`async await` 사용을 위해선 `promise` 지원이 필수적

```jsx
async function test2() {
    const hello = await doSomethingAsync();
    const world = await doAsync2(hello);
    const foo = await doAsync3(world);
    const bar = await doAsync4(foo);
    await doAsyncLast(bar);
}
```

`async await` 함수는 사용하는 여러 `promise`의 동작을 동기스럽게 사용할 수 있게 하고, 어떠한 동작을 여러 `promise`의 그룹에서 간단하게 동작하게 함

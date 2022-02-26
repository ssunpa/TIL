# Basic Concept of Promise

## Promise란?

-   비동기 작업을 하는 함수의 리턴 타입
      <aside>
      💡 함수가 비동기적인 작업을 한다. ⇒ 그 함수는 Promise를 반환한다.
      
      </aside>

-   `Resolve`와 `Reject`를 가지고 있는 객체
    -   `Resolve` : 성공했을 때 부르는 함수
    -   `Reject` : 실패했을 때 부르는 함수
-   비동기 작업 처리용 표준 인터페이스

원래는 콜백함수를 매개변수로 받아 사용

```jsx
function doSomethingAsync(onSuccess, onError) {
    //call onSuccess() or onError()
}
```

이는 콜백 지옥에 빠지기 쉬움

<aside>
💡 특정 함수에서 어떠한 역할 수행을 위해 외부 함수를 매개변수로 받아 사용하게 되는데, 이때 받아온 함수를 콜백함수라고 한다.

</aside>

```jsx
function doSomethingAsync() {
    return new Promise(function (resolve, reject) {
        //do something
        if (success) {
            resolve();
        } else {
            reject();
        }
    });
}
```

`Promise` 생성과 동시에 자동으로 실행되고 다음 중 하나의 상태를 가진다.

-   `pending` : 성공도, 실패도 하지 않은 초기 상태
-   `fulfilled` : 연산이 성공적으로 완료됨
-   `rejected` : 연산이 실패함

## Promise의 처리

-   `Promise`의 인스턴스는 `then`과 `catch` 함수를 지원
-   `Promise`의 상태가 `fulfilled`일 때 `then`을 `rejected`일 때 `catch`를 실행

```jsx
const promise = new Promise((resolve, reject) => {
    // doing some heavy work (network, read files ...)
    // using setTimeout function to simulate async code
    console.log('doing something...');
    if (success) {
        setTimeout(() => {
            resolve('success!');
        }, 2000);
    } else {
        setTimeout(() => {
            reject(new Error('someting wrong'));
        }, 2000);
    }
});

promise //
    .then((value) => {
        console.log(value);
    })
    .catch((error) => {
        console.log(error);
    });
```

`Chaining` 기능을 통해 콜백 지옥을 해결할 수 있음

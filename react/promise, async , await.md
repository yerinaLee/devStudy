
js는 싱글스레드로, 하나의 스레드에서 모든 작업이 처리되기에 한 번에 하나의 작업만 처리할 수 있다.
-> 문제 해결 : 비동기 처리


## promise

비동기 처리에 사용되는 객체. 내용은 실행되었지만 아직 결과를 반환하지 않음

```jsx
const condition = true;
const promise = new Promise((resolve, reject) => {
  if (condition) {
    resolve('resolved');
  } else {
    reject('rejected');
  }
});

promise
  .then((res) => {
    console.log(res);
  })
  .catch((error) => {
    console.error(error);
  });
```


`condition` 값의 따라 promise의 반환 값이 결정 되고 있다.

값이 참이면 `resolve` 를 호출하고, 아닐시에는 `reject` 를 호출한다.  
`resolve` 한 반환 값에 대해서는 `then()` 을 통해 결과 값을 반환 받을 수 있고 `reject` 의 반환 값에 대해서는 `catch()` 를 통해 반환 받는다.

`then()` 과 `catch()` 문의 체이닝을 통해 비동기 로직의 성공 여부에 따른 분기 처리가 가능하다.



## async, await

async : 함수 앞에 붙여 해당 함수가 비동기 함수임을 표기
await : 비동기 함수의 실행 결과를 기다리는 키워드. async 함수 안에서만 동작. 이걸 통해 promise 반환값을 받아올수있음


```jsx
(async () => {
  const condition = true;
  const promise = new Promise((resolve, reject) => {
    if (condition) {
      resolve('resolved');
    } else {
      reject('rejected');
    }
  });

  try {
    const result = await promise;
    console.log(result);
  } catch (err) {
    console.error(err);
  }
})();
```


위의 promise 코드를 async, await로 변경

await 키워드는 Promise 객체가 완료될 때까지 코드 실행을 일시 중지하므로, try-catch 블록 안에서 사용하여 에러 처리를 할 수 있다. fetch에서 네트워크 에러가 발생할 경우, await 이후의 코드는 실행되지 않으며, catch 블록으로 제어가 넘어가 에러를 처리할 수 있다.

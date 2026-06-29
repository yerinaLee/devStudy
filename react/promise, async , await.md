
js는 싱글스레드로, 하나의 스레드에서 모든 작업이 처리되기에 한 번에 하나의 작업만 처리할 수 있다.
-> 문제 해결 : 비동기 처리

promise : 비동기 처리에 사용되는 객체. 내용은 실행되었지만 아직 결과를 반환하지 않음

async : 함수 앞에 붙여 해당 함수가 비동기 함수임을 표기
await : 비동기 함수의 실행 결과를 기다리는 키워드


```
async function getData() {
  const response = await fetch('/api');
  const data = await response.json();
  return data;
}
```



await 키워드는 Promise 객체가 완료될 때까지 코드 실행을 일시 중지하므로, try-catch 블록 안에서 사용하여 에러 처리를 할 수 있다. fetch에서 네트워크 에러가 발생할 경우, await 이후의 코드는 실행되지 않으며, catch 블록으로 제어가 넘어가 에러를 처리할 수 있다.

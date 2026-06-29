
js는 싱글스레드로, 하나의 스레드에서 모든 작업이 처리되기에 한 번에 하나의 작업만 처리할 수 있다.
-> 문제 해결 : 비동기 처리


async : 함수 앞에 붙여 해당 함수가 비동기 함수임을 표기
await : 비동기 함수의 실행 결과를 기다리는 키워드


```
async function getData() {
  const response = await fetch('/api');
  const data = await response.json();
  return data;
}
```
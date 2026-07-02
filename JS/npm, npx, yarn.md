npm(Node Package Manager)과 yarn은 자바스크립트 런타임 환경인 **노드(Node.js)의 패키지 관리자**
개발자들이 js로 만든 다양한 패키지를 
npm 온라인 데이터베이스 (opens new window)에 올리면 
npm, yarn과 같은 패키지 관리자를 통해 **설치 및 삭제**가 가능



* 패키지 : npm에 업로드된 노드 모듈

차이점

npm :
- Node.js의 기본 패키지 관리자
- Node.js를 설치하기만 하면(기본적으로 npm은 Node.js 내에 내장되어 있음) cli 명령어로 기능추가 가능


yarn :
- 2016년 페이스북에서 개발한 패키지 관리자
- npm과 같은 기능을 수행하나, npm 레지스트리와 호환하면서 속도나 안정성 측면에서 npm보다 향상


![[Pasted image 20260702102426.png]]



**npx**는 npm 5.2.0 이상에서 함께 제공되는 실행 도구이다. npx의 가장 큰 장점은 패키지를 설치하지 않고도 실행할 수 있다는 점이다. 예를 들어, npx create-react-app <패키지명> 명령어를 사용하면 create-react-app을 설치하지 않고 바로 React 프로젝트를 생성할 수 있다. 또한 특정 버전의 패키지를 실행하거나, 짧은 테스트 작업을 수행하는 데 적합하다. 하지만 실행할 때마다 인터넷 연결이 필요하다는 점은 단점으로 작용할 수 있다.

출처: [https://lifewithcoding.tistory.com/283](https://lifewithcoding.tistory.com/283) [코딩이 있는 삶:티스토리]
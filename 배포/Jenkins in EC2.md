[AWS EC2에 Jenkins 서버 구축](https://velog.io/@hmyanghm/AWS-EC2%EC%97%90-Jenkins-%EC%84%9C%EB%B2%84-%EA%B5%AC%EC%B6%95)



[AWS EC2에서 Jenkins 자동배포 구축하기 (1)](https://akku-dev.tistory.com/46)


[# EC2에 젠킨스를 설치하고 배포 자동화하기](https://velog.io/@sdsd0908/EC2%EC%97%90-%EC%A0%A0%ED%82%A8%EC%8A%A4%EB%A5%BC-%EC%84%A4%EC%B9%98%ED%95%98%EA%B3%A0-%EB%B0%B0%ED%8F%AC-%EC%9E%90%EB%8F%99%ED%99%94%ED%95%98%EA%B8%B0)




---

Q. EC2 를 2개를 만들어서, 첫번째 EC2에 있는 코드 내용을 두 번째 EC2에 설치된 Jenkins로 배포하는게 가능해?

A. 네, 가능해요! 첫 번째 EC2 인스턴스에 있는 코드를 두 번째 EC2 인스턴스에 설치된 Jenkins로 배포하는 과정은 다음과 같은 단계를 포함합니다:

### 1. **첫 번째 EC2 인스턴스에 Git 저장소 설정**

- 코드가 저장된 Git 저장소를 첫 번째 EC2 인스턴스에 설정합니다.
- Git 저장소에서 코드를 Jenkins로 배포할 수 있도록 설정할 수 있습니다.

### 2. **두 번째 EC2 인스턴스에 Jenkins 설치**

- Jenkins를 두 번째 EC2 인스턴스에 설치합니다.
- Jenkins가 설치된 후, 웹 인터페이스에 접근하여 초기 설정을 완료합니다.

### 3. **Jenkins Job 설정**

- Jenkins에서 새로운 Job을 생성합니다.
- Job에서 첫 번째 EC2 인스턴스의 Git 저장소에서 코드를 가져오도록 설정할 수 있습니다.
- **Jenkins가 첫 번째 EC2 인스턴스에 접근할 수 있도록 SSH 키를 설정하거나, GitHub 등의 원격 저장소를 사용**할 수도 있습니다.

### 4. **배포 스크립트 작성**

- Jenkins Job 내에서 코드 빌드 및 배포를 자동화하는 스크립트를 작성합니다.
- 예를 들어, 빌드 후에 특정 서버에 배포할 수도 있고, Docker 컨테이너를 생성할 수도 있습니다.

### 5. **빌드 및 배포 실행**

- Jenkins Job을 수동으로 실행하거나, 코드 변경이 발생할 때 자동으로 실행되도록 설정합니다.
- Job이 성공적으로 실행되면 첫 번째 EC2 인스턴스에 있는 코드가 두 번째 EC2 인스턴스에 배포됩니다.

### 6. **자동화 및 관리**

- 필요에 따라 Jenkins Pipeline을 사용하여 더 복잡한 배포 파이프라인을 구성할 수 있습니다.
- 각 단계에서 발생하는 로그를 모니터링하고, 에러 발생 시 대응할 수 있도록 설정할 수 있습니다.

이 방법을 사용하면 첫 번째 EC2 인스턴스에서 개발된 코드를 자동으로 두 번째 EC2 인스턴스에서 배포할 수 있게 됩니다. Jenkins는 이러한 CI/CD(Continuous Integration/Continuous Deployment) 작업에 최적화되어 있어 유연하게 작업을 관리할 수 있습니다.


---




![](https://blog.kakaocdn.net/dn/neeED/btrXbtjWnuL/rK7n25rFtFD8LtcCkQRXaK/img.png)







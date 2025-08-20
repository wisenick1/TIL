CI/CD 기본개념
==

CI/CD
--
테스트, 통합, 배포를 자동화하는 것
- Github에 새로 push 할 때마다 ec2에서 pull을 땡겨서 재배포하는 귀찮음을 해결하기 위한 것
- 자동으로 push 할 때마다 자동 배포되도록 하는 것이다!

CI/CD 툴
--
- Github Actions, Jenkins, Circle CI 등 여러가지가 있지만
- 빌드용 서버가 필요없고, 무료이고, 많이 사용하는 Github Actions 굿
- 그때의 장단점을 비교하여 Github Actions vs Jenkins를 하면 된다.

> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 CI/CD 입문/실전](https://www.inflearn.com/course/비전공자-ci-cd-입문-실전/dashboard)
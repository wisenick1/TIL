Github Actions 개념 정리
==

Github Actions
--
이것도 하나의 컴퓨터라고 생각하면 편하다
- 로직을 실행시킬 수 있는 하나의 컴퓨터
- 빌드, 테스트, 배포에 대한 로직 실행

CI/CD 전체 흐름
--
큰 흐름을 보자면 이렇다.
- 코드 작성 후 commit하고 push
- 그러면 Github Actions에 작성한 로직을 실행(빌드, 테스트, 서버로 배포)
    - 방식에 따라 Github Actions에 단순히 코드만을 적고 EC2를 통해 빌드, 테스트 등이 이루어지기도 하지만 크게 생각하자면 이렇다는 의미 그리고 단순히 코드만을 적는 방식은 개인 프로젝트에 더 어울린다!!
- 서버(EC2)에서 배포된 최식 코드로 서버를 재실행

기본 문법
--

> ```
> # 이 전체를 보고 하나의 workflow 라고 하고 name은 이 workflow의 이름
> name: Github Actions 실행시켜보기
>
> # Event : 실행되는 시점을 설정
> # main 이라는 브랜치에 push 될 때 아래 workflow를 실행
> on:
>   push:
>     branches:
>       - main
>
> # 하나의 Workflow는 1개 이상의 Job 으로 구성된다.
> # 여러 Job은 기본적으로 병렬적으로 수행된다.
> jobs:
>   # Job 을 식별하기 위한 id
>   My-Depoly-job:
>     # ubuntu 환경 / 가장 최신 버전(latest)
>     runs-on: ubuntu-latest
>
>     # Step : 특정 작업을 수행하는 가장 작은 단위
>     # Job은 여러 Step 들로 구성되더 있다.
>     steps:
>       - name: Hello World 찍기
>         run : echo "Hello World"
>
>       - name: 여러 명령어 문장 작성하기
>         run: |
>           echo "Good"
>           echo "Morning"
>
>       - name: Github Action 자체에 저장되어 있는 변수 사용해보기
>         run : |
>           echo $GITHUB_SHA
>           echo $GITHUB_REPOSITORY
>
>       - name: 아무한테 노출이 되면 안 되는 값
>         run: |
>           echo ${{ secrets.MY_NAME }}
>           echo ${{ secrets.MY_HOBBY }}
> ```

> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 CI/CD 입문/실전](https://www.inflearn.com/course/비전공자-ci-cd-입문-실전/dashboard)
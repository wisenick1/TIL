dockerfile(RUN, WORKDIR, EXPOSE)
==

RUN
--
이미지 생성 과정에서 명령어 실행을 위한 것

그렇다면 ENTRYPOINT와 RUN은 어떻게 다를까?
- RUN - 이미지 생성 과정
- ENTRYPOINT - 컨테이너 생성 직후

예를 들어 ubuntu 환경에 git이 깔린 미니 컴퓨터 환경을 만들려면 ENTRYPOINT가 아니라 RUN으로 git을 설치해주어야하는 것

WORKDIR
--
작업 디렉토리 지정

WORKDIR을 /usr 이런식으로 지정하게 되면 

dockerfile 로 COPY하는 파일들이 해당 디렉터리로 정리해둔다

- WORKDIR /my-dir
- COPY ./ ./

이렇게 설정하면 현재 디렉터리의 파일들이 모두 컨테이너 내의 /my-dir 아래로 가게 된다.

작업 디렉터리를 따로 구분할 수 있다는 장점이 있다.

EXPOSE
--
포트번호 알려주기

기능 자체는 없고 문서화만 하는 용도이다!!

> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 Docker 입문/실전](https://www.inflearn.com/course/비전공자-docker-입문-실전/dashboard)
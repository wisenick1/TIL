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

- FROM
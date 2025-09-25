dockerfile(FROM, COPY, ENTRYPOINT)
==

Docker 이미지를 만들게 해주는 파일

FROM
--
베이스이미지 생성하는 역할

기본적으로 무엇을 설치할건지 정하는 명령어

만약 스프링 부트를 구동하려면 jdk가 필요한데
- FROM openjdk:17-jdk

이런식으로 기본적으로 jdk을 설치하는 이미지를 만들겠다라는 의미이다.

이를 바탕으로 이미지를 생성한다.

- docker build -t my-jdk17-server .

my-jdk17-server는 이미지 이름 .은 현재 위치 -> 현재 위치의 dockerfile을 통해 docker 이미지를 만들겠다

그 후 컨테이너를 실행시켜보면 컨테이너가 jdk를 설치하는 역할만 있기에 jdk를 설치하고 컨테이너가 종료되어 버린다. 따라서 docker ps를 쳐봐도 실행중인 컨테이너에 뜨지 않는다.

따라서 디버깅을 위해서는 ENTRYPOINT를 설정해주자.
- ENTRYPOINT ["/bin/bash", "-c", "sleep 500"]

ENTRYPOINT 는 컨테이너가 생성되고 최초로 실행할 때 수행되는 명령어

이렇게 하면 500초 동안 시스템을 일시정지 시켜 컨테이너가 실행되고 있을 수 있도록 만들어 준다.

docker logs 나 docker exec -it bash를 사용하지 않는 이유는 이 두개의 명령어는 실행중인 컨테이너에만 사용할 수 있기 때문이다!!

COPY
--
호스트 컴퓨터에 있는 파일을 복사해서 컨테이너에 전달하고 싶을 때

- COPY app.txt /app.txt

app.txt를 컨테이너 홈에 전달하겠다.

다만 앞은 상대 경로, 뒤는 절대 경로

디렉터리도 복사를 할 수 있는데 이때는

- COPY my-app /my-app/

뒤에 슬래시 하나 더 해야 디렉터리를 전달할 수 있다.

와일드카드를 이용할 수도 있고 .dockerignore에 파일을 포함시켜서 특정 파일은 전달시키지 않도록 할 수도 있다.

> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 Docker 입문/실전](https://www.inflearn.com/course/비전공자-docker-입문-실전/dashboard)
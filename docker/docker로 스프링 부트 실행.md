docker로 스프링 부트 실행
==

dockerfile을 만드는 과정과 동일하다

스프링 부트 파일 만들기
--
start.spring.io 에서 스프링 부트 파일을 만든다.

그 후 build 해서 SNAPSHOT 파일을 만들어주자.

- ./gradlew clean build

이러면 build/libs 아래 SNAPSHOT 파일이 생성된다. 

Dockerfile 생성
--
FROM을 통해 jdk를 컨테이너에 설치하고
- FROM openjdk:17-jdk

COPY를 통해 build 한 SNAPSHOT 파일을 컨테이너에 복사해주자.
- COPY build/libs/*SNAPSHOT.jar app.jar

그리고 ENTRYPOINT를 통해 복사한 파일을 실행 시켜 스프링 부트 서버를 실행시키자.
- ENTRYPOINT ["java", "-jar", "/app.jar"]

Dockerfile 빌드 후 컨테이너 실행
--
- docker build -t 이름 .
- docker run -d -p 8080:8080 이름

하면 정상적으로 서버가 실행된것을 볼 수 있다.\

> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 Docker 입문/실전](https://www.inflearn.com/course/비전공자-docker-입문-실전/dashboard)

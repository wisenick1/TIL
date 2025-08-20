EC2에 배포하기(Spring Boot)
==

기본적으로 배포는 필요한 환경 설치 -> 프로젝트 git clone -> 필요 파일 만들어주기 -> 서버 실행의 순서로 이루어진다

따라서 Spring Boot의 순서는 다음과 같다

JDK 설치&확인
--
$ sudo apt update && /

sudo apt install openjdk-17-jdk -y 로 버전에 맞는 JDK 설치

그 후, java -version으로 잘 설치됐나 확인해주자.

Github로부터 프로젝트 clone
--
git clone 프로젝트명

필요 파일 만들기
--
spring boot의 경우 application.yml 등의 설정 파일은 github에 올라가지 않게 설정하는 경우가 많다.

따라서 해댱 파일을 직접 프로젝트에 들어가서 vi를 통해 만들어주자

서버 실행
--
$ ./gradlew clean build #

$ cd ~/프로젝트명/build/libs

$ sudo java -jar 프로젝트명-0.0.1-SNAPSHOT.jar

확인
--
이후에 해당 IP에 들어가 잘 배포되었는지 확인해 보자

종료
--
비용 나가지 않게 종료 어떻게 하냐?? -> EC2 인스턴스 종료 && 탄력적 IP 릴리스

> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 AWS 입문/실전](https://www.inflearn.com/course/비전공자-이해할수있는-aws-입문실전/dashboard)
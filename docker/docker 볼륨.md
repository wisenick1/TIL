docker 볼륨
==

도커 컨테이너에 데이터를 저장해도 새로운 컨테이너로 교체 시 해당 데이터가 모두 삭제 되어버린다.

이 문제를 해결하는 것이 바로 docker 볼륨

docker 볼륨
--
- 도커 컨테이너에서 데이터를 영속적으로 저장하기 위한 방법
- 도커 컨테이너 자체 저장하는 것이 아니라 호스트 컴퓨터에 저장하는 방법을 사용한다.
- docker run -v [호스트 디렉토리 절대경로]:[컨테이너 디렉토리 절대경로] nginx
- 단, 호스트 디렉토리가 미리 만들어져 있는 경우 해당 디렉토리를 그대로 컨테이너에 복사하므로 주의가 필요하다.

MySQL 실행 예시
--
- docker run -e MYSQL_ROOT_PASSWORD=password123 -p 3306:3306 -d mysql
- 이런식으로 환경변수가 필요한 경우가 있는데 이걸 체크하자

그 이후 이 데이터베이스를 생성하고 그대로 종료하면 데이터베이스가 날아가 버린다. 따라서 볼륨을 활용해야 한다. 

앞서 말한 -v를 활용해보자.

볼륨 활용
--
폴더를 만들자. /Users/cha/Documents/Develop/docker-mysql 이런식으로 MYSQL 데이터를 저장하고 싶은 폴더를 만들자.

- run -e MYSQL_ROOT_PASSWORD=password123 -p 3306:3306 -v /Users/cha/Documents/Develop/docker-mysql/mysql-data:/var/lib/mysql -d mysql

이 명령어를 보면 만든 폴더 아래 디렉토리가 하나 더있다. 이렇게 하면 호스트 컴퓨터에 해당 디렉토리가 없으니 컨테이너에 있는 디렉토리 /var/lib/mysql의 내용을 mysql-data 로 복사한다.

참고로 /var/lib/mysql 같이 컨테이너 내의 데이터 저장장소는 docker hub의 문서를 통해 찾아봐야한다.

이렇게 컨테이너의 데이터를 호스트 컴퓨터로 공유한다.

그 후 컨테이너 삭제 후 새로운 컨테이너를 만들 때 

- run -e MYSQL_ROOT_PASSWORD=password123 -p 3306:3306 -v /Users/cha/Documents/Develop/docker-mysql/mysql-data:/var/lib/mysql -d mysql

동일한 명령어를 띄우면 이제 /Users/cha/Documents/Develop/docker-mysql/mysql-data의 데이터를 /var/lib/mysql에 덮어씌우므로 데이터가 그대로 존재하게 된다.
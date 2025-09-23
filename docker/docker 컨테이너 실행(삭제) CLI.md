docker 컨테이너 실행 CLI(+삭제)
==

docker에서 컨테이너 생성 + 실행을 같이 하고 싶을 때
- docker run nginx
이렇게 사용한다. (이미지가 없다면 docker pull도 해준다.)

그리고 docker를 그냥 실행시킬 경우 포그라운드에서 실행되게 되는데 그렇게 되면 추가적으로 명령어를 입력할 수 없다. 따라서 백그라운드로 실행시킨 후 명령어를 입력할 수 있게 하려면 -d 옵션을 사용하면 된다.

docker 백그라운드 실행(-d)
--
- docker run -d nginx

포그라운와 백그라운드
--
포그라운드 - 내가 실행시킨 프로그램의 내용이 화면에서 실행되고 출력되는 상태
백그라운드 - 내가 실행시킨 프로그램이 내부적으로 실행되는 상태


docker 컨테이너 이름 붙이기(--name)
--
- docker run -d --name my-web-server nginx

my-web-server로 이름 붙이기

docker 포트 포워딩(-p 80:80)
--
- docker run -d -p [호스트 포트]:[컨테이너 포트] nginx

이렇게 하면 내 호스트 컴퓨터에서 해당 컨테이너 포트 연결 가능

docker 컨테이너 삭제(rm)
--
- docker rm id
- docker rm $(docker ps -qa) : 중지되어 있는 모든 컨테이너 삭제
- docker rm -f $(docker ps -qa) : 실행되고 있는 모든 컨테이너 삭제

docker 로그 조회
--
- docker logs id
- docker logs -f : 컨테이너 실행시키고 실시간으로 보고 싶을 때
- docker logs --tail - -f id : tail을 활용하여 기존 로그 조회 x + 실시간 로그 조회

실행중인 컨테이너 접속하기
- docker exec -it id bash : 컨테이너 실행시키고 그 컨테이너에 접속, bash 붙이기!!

> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 Docker 입문/실전](https://www.inflearn.com/course/비전공자-docker-입문-실전/dashboard)
docker 기본 CLI
==

먼저 컨테이너에 띄워줄 이미지를 다운로드 해야한다


이미지 : 다운로드
--
- docker pull 이미지명(ex:nginx)

이렇게 하면 최신버전(latest) 이미지를 다운로드 받는다.
만일, docker hub 이미지의 tag를 보고 다른 버전을 다운로드 받고 싶다면 
- docker pull nginx:stable-perl

이렇게 다운로드 받으면 된다.

이미지 : 조회, 삭제
--
- docker image ls
- docker image rm 이미지명 or id


이제 컨테이너 이미지를 실행시킬 차례

컨테이너 생성, 실행
--
- docker create nginx
- docker start id
- 어차피 잘 안 쓰고 나중에 이미지 다운로드 + 컨테이너 생성 + 컨테이너 실행으로 docker run으로 한번에 한다.

컨테이너 조회
--
- docker ps (실행중인 컨테이너)
- docker ps -a (모든 컨테이너)

컨테이너 정지, 삭제
--
- docker stop id
- docker rm id


> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 Docker 입문/실전](https://www.inflearn.com/course/비전공자-docker-입문-실전/dashboard)
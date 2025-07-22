URI와 웹 브라우저 요청 흐름
==
> 출처 : 김영한의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-웹-네트워크/dashboard)

URI(Uniform Resource Identifier)
--
뜻 : 리소스 식별하는 통일된 방식

URI = URL + URN

URL : 리소스가 있는 위치를 지정
URN : 리소스에 이름을 부여

URL
--
프로토콜 + 호스트명 + 포트 번호 + 패스 + 쿼리 파라미터

웹 브라우저 요청 흐름
--
URL의 도메인명으로부터 DNS 조회
-> HTTP 요청 메시지 생성 -> SOCKET 라이브러리를 통해 전달(TCP/IP 연결, 데이터 전달)
-> TCP/IP 패킷 생성 -> 전달 -> HTTP 응답
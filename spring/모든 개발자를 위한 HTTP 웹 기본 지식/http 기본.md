인터넷 네트워크
==
> 출처 : 김영한의 [모든 개발자를 위한 HTTP 웹 기본 지식](https://www.inflearn.com/course/http-웹-네트워크/dashboard)

클라이언트 서버 구조
--
Request, Response 구조

클라이언트 - 서버에 요청, 응답 대기

서버 - 요청에 대한 결과 응답

무상태 프로토콜(stateless)
--
서버가 클라이언트의 상태를 보존하지 않는다.

장점 : 클라이언트가 추가 데이터를 지니고 서버로 보내기 때문에 상태를 기억하지 않아도 된다. 따라서 서버의 확장성이 높아진다.(응답 서버를 쉽게 바꿀 수 있다)

단점 : 클라이언트 추가 데이터 전송

그러나 모든 것을 무상태로 설계할 수는 없다. 따라서 최소한을 상태 유지로 설계하고 나머지를 무상태로 설계하는 방향으로!!

비연결성(connectionless)
--
HTTP는 기본적으로 연결을 유지하지 않는 모델로 서버 자원을 매우 효율적으로 사용할 수 있다.

그러나 시간 추가, 자원 다운로드의 한계가 있다.

초기 http는 자원 요청 응답에 시간이 꽤 소요됐지만, http지속 연결을 통해 자원 요청 응답이 한 연결 내에 이루어지도록 하여 개선시켰다.

HTTP 메시지
--
HTTP 메시지 구조
- start-line 시작 라인
- header 헤더
- empty line 공백 라인 (CRLF)
- message body

요청 메시지
- start-line = request-line
- http 메서드 + 요청 대상 + HTTP version

- header : host

- (message body)

응답 메시지
- start-line = status-line
- HTTP version + 상태 코드 + 이유

- header : 전송에 필요한 부가 정보

- message body : 전송 데이터


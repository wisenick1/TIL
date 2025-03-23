JDBC 이해
==
> 출처 : 김영한의 [스프링 DB 1편 - 데이터 접근 핵심 원리](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-db-1/dashboard)

애플리케이션 서버와 DB는 일반적으로 커넥션 연결, SQL 전달, 결과 응답의 과정으로 이루어진다.

그러나 문제는 DB마다 각 과정의 방법이 모두 다르다!

이를 해결하기 위해 JDBC 표준 인터페이스가 만들어졌다 -> JDBC의 기능만 구현하면 된다.

이 JDBC를 편리하게 사용하기 위해 SQL Mapper(SQL 전달)와 ORM 기술(객체 전달)이 나왔지만 결국 JDBC가 이용되기에 이를 어느정도 알아두는게 필요!

JDBC DriverManager
--
DB연결 과정을 살펴보자.
- JDBC는 java.sql.Connection 인터페이스를 제공한다.
- JDBC가 제공하는 DriverManager는 URL정보를 확인하여 DB로부터 커넥션을 획득
- 커넥션을 획득할 때 해당 DB드라이버는 위의 Connection 인터페이스를 구현한 구현체 제공(h2는 org.h2.jdbc.JdbcConnection)

이후 과정
--
- 위에서 얻은 구현체를 활용하여 Statement를 활용하여 데이터베이스에 전달할 SQL과 파라미터로 전달할 데이터들을 준비
- 데이터 지정 후 crud
- 결과 응답이 필요한 경우 ResultSet 활용
- :punch: 주의! - Connection, Statement, ResultSet 사용 후 해당 순서대로 close()해줘야한다.


정리
--
- JDBC는 각 DB마다 다른 세부과정을 편리하게 하기 위해 만든 것
- JDBC의 DriverManager로 얻은 알맞은 DB드라이버를 통해 conntion이 이루어진다.
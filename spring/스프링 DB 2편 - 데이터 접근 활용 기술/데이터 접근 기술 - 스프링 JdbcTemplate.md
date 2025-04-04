데이터 접근 기술 - 스프링 JdbcTemplate
==
> 출처 : 김영한의 [스프링 DB 2편 - 데이터 접근 활용 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-db-2/dashboard)

SQL을 직접 사용하는 경우 좋은 선택지이다.
다만 동적 SQL을 해결하기 어렵다.

JdbcTemplate
--
- dataSource를 통해 JdbcTemplate을 사용한다.
- 데이터 저장 시 auto increment방식을 사용하면 DB에서 id를 생성한다. 따라서 생성된 id를 db에서 가져와야 함 - 이 때 keyHodler가 사용된다.

JdbcTemplate - NamedParameterJdbcTemplate
--
- SQL에 ?를 사용할 시 값을 순서에 맞추어 넣어줘야하는데 이 경우 오류가 생길 가능성이 다분하다!
- 이때 NamedParameterJdbcTemplate을 사용하면 되는데 객체의 필드 변수를 파라미터이름으로 넣을 수 있도록 지정해준다.
- SQL 파라미터 지정방법 3가지
    - BeanPropertySqlParameterSource(객체) - 자바빈 프로퍼티 규약
    - MapSqlParameterSource().addValue(필드변수)
    - Map.of(필드 변수) - 단순 Map
- RowMapper() 또한 BeanPropertyRowMapper를 활용할 수 있다.

JdbcTemplate - SimpleJdbcInsert
--
- Insert의 경우 key를 고려해야하기 때문에 복잡해지는데 SimpleJdbcInsert를 통해 간단히 만들 수 있다.
- 생성자에서 지정을 해주면 SQL을 작성하지 않고도 SQL만들어서 실행도 해주고 key도 return 해준다.

정리
--
JdbcTemplate
- NamedParameterJdbcTemplate와 Insert시 SimpleJdbcInsert 활용!
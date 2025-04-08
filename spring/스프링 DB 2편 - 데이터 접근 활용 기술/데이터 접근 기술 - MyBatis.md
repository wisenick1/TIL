데이터 접근 기술 - MyBatis
==
> 출처 : 김영한의 [스프링 DB 2편 - 데이터 접근 활용 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-db-2/dashboard)

JdbcTemplate과 비교해 SQL, 동적 쿼리의 작성이 메우 편리하다.

MyBatis 설정
--
- JdbcTemplate과 다르게 gradle에 추가 필요
- xml내에 resultType등을 쓸 때 package원래 모두 써야 하나 mybatis.type-aliases-package=~~ 이걸 통해 패키지를 지정해 줄 수 있다.
- map-underscore-to-camel-case을 활성화 하면 언더스코어 표기를 자동으로 카멜로 변환해준다.

MyBatis 적용
--
- 구현체를 사용하지 않고 Mapper 인터페이스(@Mapper 사용)를 만들어주면 된다!(Proxy객체를 통해 알아서 만들어서 스프링 빈으로 등록한다)
- Mapper 인터페이스와 같은 패키지 위치에 Xml파일을 만들어 SQL문과 동적 쿼리를 작성
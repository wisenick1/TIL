데이터 접근 기술 - Querydsl
==
> 출처 : 김영한의 [스프링 DB 2편 - 데이터 접근 활용 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-db-2/dashboard)

버전마다 QueryDSL의 build.gradle의 설정이 조금씩 다를 수 있으니 querydsl gradle을 검색하여 확인하자

QueryDSL
--
- JPA쿼리(JPQL)을 typesafe하게 작성하는데 사용된다
- @Entity를 통해 해당 클래스의 Q 타입을 생성시켜 준다.
- 이 Q 타입을 통해 사용
- 쿼리 문장 오타를 컴파일 시점에 막을 수 있다.
- 코드 재사용 가능
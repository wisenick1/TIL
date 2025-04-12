데이터 접근 기술 - JPA
==
> 출처 : 김영한의 [스프링 DB 2편 - 데이터 접근 활용 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-db-2/dashboard)

객체답게 모델링하기 위해 등장한 것이 JPA

JPA
--
- JPA 설정 추가
- JPA가 사용하는 객체임을 알리기 위해 @Entity로 인식시켜 주자
- EntityManager를 통해 테이블을 저장, 조회 등을 수행
- 복잡한 조건으로 조회 시 JPQL을 사용한다.

JPA 예외
--
EntityManager에서 예외가 발생 시 JPA관련 예외가 발생한다.
따라서 예외가 스프링의 예외 추상화(DataAccessException)로 변환되어야하는데 이것을 @Repository가 해준다.
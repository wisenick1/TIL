순수 JPA와 Querydsl
==
> 출처 : 김영한의 [실전! Querydsl](https://www.inflearn.com/course/querydsl-실전/dashboard)

JPAQueryFactory를 사용하려면 생성자 주입 방식으로 주입하지만 @RequiredArgs~~를 쓰기 어렵다

따라서 이를 사용하기 위해서는 스프링 빈으로 등록하여 주입 받아 사용해도 된다.

프로파일 설정
--
application.yml등의 설정 파일에
> spring: profiles: active: 에 local, test, dev등으로 프로파일을 설정하면 소스코드 실행시 프로파일을 분리할 수 있다.

분리하고 싶은 클래스에 @Profile("test") 이런식으로 설정
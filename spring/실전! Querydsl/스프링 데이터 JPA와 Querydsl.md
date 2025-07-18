스프링 데이터 JPA와 Querydsl
==
> 출처 : 김영한의 [실전! Querydsl](https://www.inflearn.com/course/querydsl-실전/dashboard)

앞서 정리했듯 따로 사용자 정의 repository를 만들어서 Querydsl을 작성해야 한다.

동적 쿼리의 경우 모두 null 값이 들어가면 모든 정보를 불러와야 하므로 페이징을 활용하는 것이 좋다.

또한 Count 쿼리를 left Join 등이 필요 없을 수도 있으니 이를 활용하여 페이징을 작성하자.

페이징 작성법
--
dto를 조회하는 쿼리와 count 쿼리를 작성하여
new PageImpl<>()을 반환해 준다.

추가적으로 PageImpl 대신 PageableExcutionUtils.getPage를 활용하면 첫 페이지 사이즈 보다 불러올 컨텐츠 사이즈가 작을 때, 마지막 페이지 일 때 countQuery를 생략하도록 처리할 수 있다.
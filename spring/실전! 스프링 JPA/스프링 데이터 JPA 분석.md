스프링 데이터 JPA 분석(+em.save)
==
> 출처 : 김영한의 [실전! 스프링 JPA](https://www.inflearn.com/course/스프링-데이터-JPA-실전/dashboard)

em.save()
--
- 새로운 엔티티면 저장(persist)
- 새로운 엔티티가 아니면 병합(merge)

식별자의 null, 0의 여부로 새로운 엔티티인지 판단한다.

그러나, 여기서 문제는 Id값을 직접 주는 상황일 경우, save 시점에 객체의 식별자 값이 null이 아니므로 새로운 엔티티를 저장할 때 save가 아닌 merge가 호출된다. - 이는 매우 비효율적

따라서 Persistable 을 구현하여 새로운 객체인지 판별해주는 로직을 작성하여 save를 호출하게 만들자!!
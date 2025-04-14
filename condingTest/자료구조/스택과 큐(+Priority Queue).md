스택과 큐(+Priority Queue)
--
> 출처 : [Do it! 알고리즘 코딩테스트 with JAVA](https://www.inflearn.com/course/%EB%91%90%EC%9E%87-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%EC%BD%94%EB%94%A9%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%9E%90%EB%B0%94/dashboard)


스택
- peek : top요소 확인
- push, pop: top에 추가, 제거

큐
- peek : front요소 확인
- poll : front에 제거
- add : rear에 추가

우선순위 큐
- add: 요소 추가
- poll : 요소 제거
- 큰 수, 작은 수 기준은 Collections.reverseOrder()로 간단하게 가능
- 람다를 통해 자체적으로 기준을 만들어 정렬시킬 수 있다!!!!! - [백준 11286번](https://github.com/wisenick1/baekjoon/tree/main/%EB%B0%B1%EC%A4%80/Silver/11286.%E2%80%85%EC%A0%88%EB%8C%93%EA%B0%92%E2%80%85%ED%9E%99)



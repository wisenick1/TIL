조회와 정렬
==
> 출처 : 김영한의 [실전 데이터베이스 입문 - 모든 IT인을 위한 SQL 첫걸음(SQL부터 차근차근)](https://www.inflearn.com/course/김영한-실전-데이터베이스-입문/dashboard)

select
--
필요한 정보만 보고 싶다면
- SELECT name, price FROM products;

별칭을 붙이고 싶다면
- SELECT name as 이름, price as 가격 FROM products;

특수문자가 들어가 별칭을 붙이고 싶다면 -> 백틱 이용(`)
- SELECT name as '`제품 이름`' FROM products;

where(조건)
--
여러 조건들을 사용할 수 있다. between, in, like 만 정리하자면

가격 1000, 5000원 사이이면
- WHERE price BETWEEN 1000 AND 5000;

여러 개 중 고르는 거면
- WHERE product_id IN (1, 2, 3);

like는 %, _ 사용

order by
--
정렬 조건이 여러 개일 때
- ORDER BY price DESC, stock_quantity;

limit
--
개수 제한에도 사용하지만 페이징 처리에 사용
- LIMIT OFFSET, row_count;

offset은 건너뛰는 개수, row_count는 가져오는 개수

3개씩 가져온다고 했을 때, 페이지 별로 보면

1 페이지
- LIMIT 0, 3;

참고로 이렇게도 쓸 수 있다.
- LIMIT 3 OFFSET 0

2 페이지(앞에 3개 건너뛰고 3개 가져오기)
- LIMIT 3, 3;

3 페이지(앞에 6개 건너뛰고 3개 가져오기)
- LIMIT 6, 3;

offset 공식을 세워 보자면(페이지당 가져오는 개수가 같을 때)
- offset = (페이지 번호 - 1) * row_count

distinct
--
중복 제거

- select 보다 성능 저하가 있을 수 있으나 크게 문제가 되지는 않는다.

NULL
--
이건 어떤 값이 아니라 알 수 없는 값이라는 뜻이다. 등호를 통한 비교 등이 불가능하다.

따라서 IS NULL, IS NOT NULL 등을 통해 NULL을 검사해야 한다.

NULL 정렬은 기본적으로 가장 작은 값으로 취급되어 정렬된다.

따라서 asc는 값이 가장 먼저 나오고, desc는 값이 제일 마지막에 나오는데

필요에 따라 null 값의 위치 조정이 필요할 수 있다 :rocket: **이럴 때는 is null을 활용하여 order by를 통해 조작하자.**

예를 들어 description을 내림차순으로 정렬하고 싶을 때, null인 row들을 가장 먼저 나오게 하고 싶다면

- SELECT name, description, description IS NULL FROM products ORDER BY description IS NULL desc, description desc;

이렇게 하여 null인 row들이 먼저 나오게 하고 null 이 아닌 row들이 정렬되도록 하면 된다.

참고로, select 문에 꼭 description IS NULL 이 들어갈 필요는 없다.

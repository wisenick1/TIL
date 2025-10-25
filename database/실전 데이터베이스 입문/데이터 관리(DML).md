데이터 관리(DML)
==
> 출처 : 김영한의 [실전 데이터베이스 입문 - 모든 IT인을 위한 SQL 첫걸음(SQL부터 차근차근)](https://www.inflearn.com/course/김영한-실전-데이터베이스-입문/dashboard)

등록
--
INSERT INTO 테이블명 () VALUES ();

:rocket: **추가할 열의 목록을 항상 명시적으로 쓰자!!!**
- 테이블 명 뒤의 열의 목록을 항상 써주기
- 테이블 구조가 변경될 시 오류를 일으키기 때문에 무조건 써주자

수정
--
UPDATE 테이블명 SET 변경내용 WHERE 조건
- UPDATE products SET price = 1000 where product_id = 1;

:rocket: **아주 주의해야할 점이 있는데 where가 빠지면 안된다**

안전 업데이트 모드를 제공하기 때문에 기본적으로 where가 없을 경우 에러가 나지만 default가 OFF일 수도 있음

이 안전 업데이트 모드는 workbench에서는 기본적으로 켜져있는데
- SET SQL_SQFE_UPDATES = 0;

을 통해 비활성화가 가능하고 기본 설정 또한 변경이 가능하다.

실제로 이 안전 업데이트 모드를 비활성화하고 UPDATE products SET price = 1000; 이런 SQL문을 실행시키면 products 테이블의 price가 모두 1000으로 바뀐다!!!

따라서 수정 시에는 안전하게 습관을 들이는 것이 좋다.

먼저 변경 대상을 확인하자
- SELECT * FROM products where name = '';

이렇게 확인을 하고 위의 where 부분을 그대로 활용하여
- UPDATE products SET price = 9000 where name = '';
하여 업데이트 해주자!!!

삭제
--
DELETE FROM 테이블명 WHERE 조건
- DELETE FROM products where product_id = 1;

이것도 수정처럼 안전 업데이트 모드가 있으나 활성화가 되어있지 않을 때 where가 없다면 대참사 발생!!!

DELETE vs TRUNCATE
- 하나씩 삭제(느림) vs 한번에 다 삭제(빠름)
데이터 관리(DDL)
==
> 출처 : 김영한의 [실전 데이터베이스 입문 - 모든 IT인을 위한 SQL 첫걸음(SQL부터 차근차근)](https://www.inflearn.com/course/김영한-실전-데이터베이스-입문/dashboard)

테이블 생성
--
CREATE TABLE customers (); 을 통해 테이블을 생성하자.
- DATETIME DEFAULT CURRENT_TIMESTAMP

이렇게 하면 DATETIME 값을 넣지 않아도 현재 시간이 들어간다.

**외래키 제약 조건 넣어주기**
- 제약 조건의 이름은 테이블의 이름을 명시해주는 것이 좋다
- orders 테이블에서 customers 테이블의 customer_id를 참조하는 상황이라면 fk_orders_customers 이런식으로 제약 조건의 이름을 지어주자.
- CONSTRAINT fk_orders_customers FOREIGN KEY (customer_id) REFERENCES customers(customer_id)

ERD 만들기
--
MYSQL 워크벤치의 상단 메뉴바 Database > Reverse Engineer를 클릭하여 생성!

테이블 변경, 제거
--
ALTER TABLE customers 을 기본적으로 사용한다.

열 추가
- ADD COLUMN point INT NOT NULL DEFAULT 0;

열 데이터 타입 변경
- MODIFY COLUMN address VARCHAR(400) NOT NULL;

열 제거
- DROP COLUMN point;

:rocket: **ALTER 아주 조심해서 사용해야 한다**
- 열 추가 정도는 시간이 걸리지 않으나 다른 작업들은 서비스가 일정 시간 멈출 수도 있다!!

DROP vs TRUNCATE
--
DROP - 다 날리기
TRUNCATE - 테이블은 남겨주고 데이터 다 날리기
- TRUNCATE와 DELETE 차이를 보면 DELETE는 한 줄씩, TRUNCATE는 한번에 초기화해서 TRUNCATE가 더 간단하고 빠르다!!

참고로 DROP, TRUNCATE는 참조 당하는 테이블에서는 사용할 수 없다. orders가 products를 참조하고 있다면 products에서는 두 명령어를 사용할 수 없다.

따라서 한방에 날리고 싶다면
- SET FOREIGN_KEY_CHECKS = 0;

으로 외래 키 체크를 비활성화하여 DROP 혹은 TRUNCATE를 사용해주자.

단, 0으로 설정한 후에는 다시
- SET FOREIGN_KEY_CHECKS = 1;

로 다시 활성화시켜주어야 한다.
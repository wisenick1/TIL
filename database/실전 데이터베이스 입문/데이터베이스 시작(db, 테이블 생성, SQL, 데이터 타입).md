데이터베이스 시작(db, 테이블 생성, SQL)
==
> 출처 : 김영한의 [실전 데이터베이스 입문 - 모든 IT인을 위한 SQL 첫걸음(SQL부터 차근차근)](https://www.inflearn.com/course/김영한-실전-데이터베이스-입문/dashboard)

MYSQL 간단 사용법 알기
-- 
데이터베이스 생성
- CREATE DATABASE 데이터베이스 이름;

작업할 데이터베이스 선택
- USE 데이터베이스 이름;
- workbench 다시 시작 시에도 써주어야한다.

테이블 생성
- CREATE TABLE 테이블 명 (~ ~ ~);
- CREATE TABLE sample ( product_id INT PRIMARY KEY );

이런식으로 생성한다

참고로, 테이블에는 반드시 기본 키(PRIMARY KEY)가 있어야 한다.

테이블 구조 확인
- DESCRIBE 테이블 명

주석
- SQL 앞에 --와 공백을 넣으면 된다.

데이터베이스, 테이블 목록 보기
- SHOW DATABASES;
- SHOW TABLES;

데이터베이스, 테이블 영구 삭제
- DROP TABLE 테이블 명;
- DROP DATABASE 데이터베이스 명;

기본 CRUD는 익숙하니 패스

SQL이란?
==
앞서 배운 명령어들의 집합

- SQL은 관계형 데이터베이스의 표준 언어

SQL 표준을 넘어 각 DBMS의 추가 기능이나 문법을 Dialect라고 한다.

- SQL은 선언적 언어이다. 어떻게 데이터를 가져올지 지시하는 것이 아니라 무엇을 원하는지만 명시하면 된다!!

SQL 명령어 4가지 종류
- DDL(정의어), DML(조작어), DCL(제어어), TCL(트랜잭션 제어어)




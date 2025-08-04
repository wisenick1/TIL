RDS 만들기
==

RDS
--
관계형 데이터베이스 서비스
- DB도 외부 인터넷에서 접근할 수 있도록 해주어야 함
- EC2 내에 직접 DB를 설치할 수도 있지만 백엔드 서버 장애로 EC2가 죽을 경우 DB도 같이 죽어버리는 경우가 발생한다.
- 따라서 RDS를 활용하는 것이 편리한 기능도 많아, RDS를 활용해 인프라를 구성하는 것이 좋다.

RDS 생성하기
--
1. RDS 리전 선택
2. 데이터베이스 종류 선택
3. 템플릿 선택(프리 티어 쓰자~~)
4. 설정(이름, DB 암호 설정) - 사용자 이름과, 암호는 따로 적어두도록 하자
5. 연결 - 퍼블릭 엑세스를 예로 하여도 그리 치명적인 문제가 발생하지는 않는다, 공부를 더하면 아니오로 해서 구성해보기

보안 그룹 설정하기
--
이제 RDS자체의 보안그룹을 설정할 차례
1. EC2내의 보안그룹 만들기
2. 인바운드 규칙 추가(선택한 DB) - RDS의 MySQL은 포트 3306번 -> 보안그룹 생성
3. 생성한 RDS로 가서 생성한 보안그룹 붙여주기 - 연결에 보안그룹

파라미터 그룹 추가하기
--
1. RDS 파라미터 그룹 생성
2. 세부 정보를 설정해 준다.
3. character 관련 속성 -> utf8mb4(한글 + 이모티콘), collation관련 속성 -> utf8mb4_unicode_ci(졍렬, 비교방식), time_zone -> Asia/Seoul
4. 생성한 RDS로 가서 추가 구성에 파라미터 그룹 넣어주기
5. 재부팅하기

springboot 설정
--
application.yml 내에
> ```
> server:
>   port: 80
> spring:
>   datasource:
>     url: jdbc:mysql://___________:3306/instagram # RDS 인스턴스 엔드포인트
>     username: ______ # RDS 마스터 사용자 이름
>     password: ______ # RDS 마스터 암호
>     driver-class-name: com.mysql.cj.jdbc.Driver
>   jpa:
>     hibernate:
>       ddl-auto: update
>     show-sql: true
> ```
이런식으로 설정하고 RDS와 연결이 잘 되는지 확인해 보도록 하자

종료
--
최종 스냅샷 생성, 자동 백업 보존 체크 해제


> 출처 : JSCODE 박재성의 [비전공자도 이해할 수 있는 AWS 입문/실전](https://www.inflearn.com/course/비전공자-이해할수있는-aws-입문실전/dashboard)

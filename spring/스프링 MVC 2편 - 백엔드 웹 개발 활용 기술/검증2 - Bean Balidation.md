검증2 - Bean Validation
==
> 출처 : 김영한의 [스프링 MVC 2편 - 백엔드 웹 개발 활용 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-mvc-2/dashboard)

객체 클래스에 직접 적용
--
- 검증1에서 로직을 일일이 짜면 검증 코드가 너무 복잡한 것을 보았다.
-> 객체 클래스에 필드에 직접 애노테이션 적용
- 스프링 부트의 LocalValidatorFactoryBean으로 @Validated를 통해 적용
- 바인딩 성공한 필드만 BenaValidation 적용
    -필드 각각 reject 해줬던거 생각하면 될 듯
- ObjectError도 처리하는 방법이 있지만 그건 코드 직접 짜는 것을 권장
    -검증 기능이 해당 객체 범위를 넘어서는 경우가 종종 등장한다.

폼마다 요구사항이 다를 시
--
- groups
    - 애노테이션에 groups 지정하기
- 전송 객체 분리
    - 폼마다 객체를 따로따로 생성하기

정리
--
build.gradle 추가에 추가
폼별로 객체 따로따로 생성


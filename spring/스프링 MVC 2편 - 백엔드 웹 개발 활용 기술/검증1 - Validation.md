검증1 - Validation
==
> 출처 : 김영한의 [스프링 MVC 2편 - 백엔드 웹 개발 활용 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-mvc-2/dashboard)

컨트롤러의 중요한 역할 중 하나 - HTTP 요청이 정상인지 검증하는 것

검증 로직을 단순화해가는 과정

1. 그냥 저장
- 검증 오류 결과를 보관할 자료 구조를 통해 검증 로직에 따른 key(어떤 필드 오류)와 value(오류 메시지) 담아주고, 그걸 통해 검증
- 타입이 다른 값에 대한 처리가 안된다.


2. BindingResult 등장
- 검증 오류 결과 보관할 자료 구조 필요 없음
- 특정 필드 예외 bindingResult.addError(FieldError)
- 전체 예외 bindingResult.addError(ObjectError)
- :rocket: 위치 중요 - @ModelAttribute 뒤!!
- 알아서 item에 바인딩까지 된다!

    2.1 BindingResult의 힘
    - 1에서 문제였던 타입이 다른 값이 바인딩 될 시 오류가 발생해도 컨트롤러 호출!

    2.2 FieldError와 ObjectError
    - 생성자 내 rejectedValue 값이 없으면 사용자의 입력 값이 유지되지 않는다.

3. 오류 메시지를 한 곳에서 다뤄보자
- properties 파일을 활용하여 값에 오류 메시지를 넣는다
- 그 후 FieldError와 ObjectError 생성자 파라미터를 활용한다.
4. reject를 사용해 FieldError와 ObjectError 없애기 
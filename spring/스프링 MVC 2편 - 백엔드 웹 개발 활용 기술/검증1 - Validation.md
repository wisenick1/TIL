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
- defaultMessage도 삭제 가능!
4. rejectValue(), reject를 사용해 FieldError와 ObjectError 없애기
- bindingResult가 어떤 객체를 대상으로 검증하는지 아는데 굳이 줘야하나!
- 관련 파라미터 제거 가능!
- 어떻게 errorCode를 이렇게 간단히 줘도 될까?
    - MessageCodesResolver!
5. MessageCodesResolver
- errorCode가 알아서 생성해서 보관한다
- rejectValue(), reject가 이 MessageCodesResolver를 가지고 있다
- properties에 범용적인 메시지를 먼저 넣고 필요에 따라 구체적인 메시지를 작성하는 것이 좋다.
- 이렇게 하여 스프링에서 자동생성하는 typeMisMatch에 대해서도 오류 메시지 지정 가능
6.  Validator 분리
- 검증 로직을 분리
- 어떤 검증기를 실행할지 구분하고, validate 실행

:rocket: 정리
--
 직접 생성 -> BindingResult -> Validator 분리 플로우를 익히자

API 예외 처리
==
> 출처 : 김영한의 [스프링 MVC 2편 - 백엔드 웹 개발 활용 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-mvc-2/dashboard)

HTTP API의 데이터 처리 시 HTML 페이지가 아닌 JSON이 반환되기를 원한다.

앞서 활용했던 BasicErrorController를 통해 HTML페이지 처리는 매우 간단하지만 API 처리는 매우 복잡할 수 있다.

BasicErrorController 활용 방식 - HandlerExceptionResolver
--
- ModelAndView를 반환하여 Exception을 정상 흐름처럼 변경한다.
- 예외 코드 변환 등이 가능
- WAS까지 예외를 던지지 않고 여기에서 해결 가능(다만, BasicErrorController까지 도달하지 않고 ModelAndView를 반환하기 때문에 JSON반환 시 자체적으로 열심히 JSON으로 바꿔줘야한다)

ExceptionResolver 활용
--
- ExceptionHandlerExceptionResolver을 활용
- API 예외를 다루는 가장 적합한 방식
- 예외에 따른 다른 데이터 출력 등 모두 편리
- @ExceptionHandler를 통해 예외를 지정
- 아주아주 편리하게 @ControllerAdvice를 통해 예외들을 한번에 처리, 대상 지정 등을 자유자재로 할 수 있다.

정리
--
:rocket:API 예외 -> @ExceptionHandler 써라
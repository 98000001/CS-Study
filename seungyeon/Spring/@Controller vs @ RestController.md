# @Controller vs @ RestController

### @Controller

- Spring MVC 의 컨트롤러인 @Controller는 View를 반환하기 위해 사용.
- Spring MVC 컨트롤러를 사용하며 Data를 반환해야하는 경우, 데이터를 반환하기 위해 @ResponseBody 어노테이션을 사용해야함.
    - 기존에는 Json 형태 반환 불가능. @ResponseBody를 통해 Json 형태 데이터 반환 가능
    - 객체 반환 시 ViewResolver 대신 HttpMessageConverter 동작

### @RestController

@Controller + @ResponseBody

- Json 형태로 객체 데이터를 반환하기 위해 사용. 최근 데이터를 응답으로 제공하는 REST API 개발 시 주로 사용
- 객체를 ResponseEntity로 감싸 반환
    - 상황에 맞는 HttpStatus를 설정해 객체 반환 할 수 있도록
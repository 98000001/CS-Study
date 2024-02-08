HTTP Response Body가 생성되는 방식의 차이


@Controller의 역할은 Model 객체를 만들어 데이터를 담고 View를 반환
@RestController는 단순히 객체만을 반환하고 객체 데이터는 JSON 또는 XML 형식으로 HTTP 응답에 담아 전송
즉 @Controller와 @ResponseBody의 동작을 조합한 @RestController
##### RestController를 표시하면 모든 메소드가 뷰 대신 객체로 작성됨

#### 일반적인 Spring MVC Work-flow
Controller - View
Controller는 주로 View를 반환하기 위해 사용
Controller가 View를 반환하기 위해서는 View Resolver가 사용되며, ViewResolver 설정에 맞게 View를 찾아 렌더링 합니다.

Controller - Data
데이터를 반환하기 위해 @ResponseBody 어노테이션을 사용해주면, 이를 통해 Controller도 JSON 형태로 데이터를 반환



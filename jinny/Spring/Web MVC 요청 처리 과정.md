## Web MVC 요청 처리 과정(DispatcherServlet을 중심으로)
디스패처서블릿은 HTTP 요청들을 매핑된 컨트롤러로 배차해주는 역할을 수행하는 중앙 서블릿

### Front-Controller 패턴
적용하면 다수의 서블릿이 아닌 하나의 프런트 컨트롤러 서블릿으로 다수의 클라이언트 요청을 받을 수 있음
다양한 HTTP 요청에 대해 공통 처리가 가능하여 코드 재사용성과 유연성을 높이며 중복 줄임
또한 중앙 집중식 제어를 통해 보안이 강화되며 사용자 트랙킹에도 유리

## DispatcherServlet의 동작 원리
DispatcherServlet은 다음과 같이 HttpServlet을 상속받아서 사용하기 때문에

서블릿이 호출되면 HttpServlet.service() -> FrameworkServlet.service() -> DispatcherServlet.doDispatch()가 호출

<img width="666" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/f092d7b9-fc01-4d36-8299-f19318d50d0d">

스프링 애플리케이션이 실행되면 DispatcherServlet을 자동으로 등록 ->
컴포넌트 스캔을 통해 @RequestMapping 어노테이션이 있는 핸들러들을 모두 매핑 ->
Http요청이 들어오면 DispatcherServlet은 HandlerMapping에서 요청과 매핑된 핸들러를 조회하고 가지고 옴(+ 매핑된 핸들러를 찾지 못하면 noHandlerFound() 메서드)->
HandlerAdapter 목록에서 support() 메서드(해당 어댑터가 매개변수로 주어진 핸들러를 지원하는 여부를 판별하는 메서드)를 통해 일치하는 HandlerAdapter를 찾아 가지고 옴 ->
HandlerAdapter를 통해 handle() 메서드를 호출하고 이 안에서 비즈니스 로직이 실행. HandlerAdapter는 리턴 값으로 viewname과 model을 반환 ->
ViewResolver를 통해 viewName을  실제 view로 반환->
render메서드를 통해 view를 생성하고 HTTP 응답 메시지를 생성하여 클라이언트에게 반환




# Web MVC 요청 처리 과정.(DispatcherServlet을 중심으로)

## Spring MVC

Model-View-Controller 로, 사용자 인터페이스와 비즈니스 로직을 분리해 웹 개발을 하는 것

- Model
    - 애플리케이션의 정보, 즉 데이터
    - 일반적으로 POJO, Java Beans
- View
    - 사용자에게 보여주는 인터페이스, 즉 화면
    - Model Data 렌더링. HTML 을 생성
    - JSP,Thymeleaf, Groovy 등의 template engine
- Controller
    - View 와 Model 사이의 인터페이스 역할
    - Model Object와 Model을 화면에 출력할 View name 반환

### Spring 이 제공하는 Class?

- DispatcherServlet
    - Spring 이 제공하는 Servlet 클래스
    - 클라이언트의 요청을 처음으로 받는 클래스
    - Dispatcher가 받은 요청은 HandlerMapping으로 넘어감
- HandlerMapping
    - 사용자의 요청을 처리할 Controller를 찾음
    - 요청 url 에 해당하는 Controller 정보를 저장하는 table을 가짐
    - 클래스에 @RequestMapping(”/url”) 명시하면 해당 url 에 대한 요청이 들어왔을 때 table에 저장된 정보에 따라 해당 클래스 또는 메소드에 매핑함
- ViewResolver
    - Controller가 반환한 View Name에 prefix, suffix 를 적용해 View Object 반환
        - 해당하는 View에 Controller에게 받은 Model 전달
        - View name : home 이면 prefix : /WEB-INF/views, suffix:.jsp는 "/WEB-INF/views/home.jsp"라는 위치의 View에 Controller에게 받은 Model을 전달
        - 이후 해당 View에서 Model Data를 이용해 적절한 페이지를 만들어 사용자에게 보여줌

### Spring MVC 패턴 처리 과정


1. 클라이언트가 서버에 요청하면, DispatcherServlet이 요청을 가로챈다.
2. 요청을 가로챈 DispatcherServlet은 HandlerMapping에게 요청을 위임할 Controller를 물어본다
    1. servlet-context.xml에 @Controller로 등록된 것들을 스캔해 찾아준다
3. 요청에 매핑된 Controller가 있다면 @RequestMapping을 통해 요청을 처리할 메소드에 도달한다
4. Controller에서는 요청을 처리할 Service를 주입받아 비즈니스 로직을 Service에 위임한다
5. Service에서는 요청에 필요한 작업을 담당하며 모든 로직을 끝낸 서비스가 결과를 Controller에 넘긴다
6. 결과를 받은 Controller는 Model 객체에 어떤 View를 보여줄 것인지 정보를 담아 DispatcherServlet 에 보낸다

6-1. Controller는 요청을 처리한 후 객체를 반환한다. 반환된 객체는 JSON으로 직렬화 되어 클라이언트에 반환된다.

1. DispatcherServlet은 ViewResolver에게 View에 대한 정보를 넘긴다.
2. ViewResolver는 해당 JSP를 찾아 DispatcherServlet에 알려준다
3. DispatcherServleet은 응답할 View를 Render를 지시하고, View는 응답 로직을 처리한다
4. 결과적으로 DispatcherServlet이 클라이언트에게 렌더링된 View를 응답한다
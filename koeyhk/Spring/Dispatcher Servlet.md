## **Dispatcher Servlet**

- **HTTP 프로토콜로 들어오는 모든 요청을 가장 먼저 받아 적합한 컨트롤러에 보내주는 `Front Controller`**
    - `Front Controller` 는 주로 서블릿 컨테이너의 제일 앞단에서 서버로 들어오는 클라이언트의 모든 요청을 받아서 처리해주는 컨트롤러 ( MVC 구조에서 함께 사용되는 디자인 패턴 )
- `Dispatcher Servlet`은 해당 어플리케이션으로 들어오는 모든 요청을 핸들링 해주기 때문에, 우리는 컨트롤러를 구현해두기만 하면 `Dispatcher Servlet`가 알아서 적합한 컨트롤러로 위임을 해주는 구조

<br>

### **Dispatcher Servlet의 동작 과정**

<img src="https://github.com/98000001/CS-Study/assets/80199502/02e908a1-ea0d-4576-b1b0-a177ca445c5d"  width="700">

1. 클라이언트의 요청을 `Dispatcher Servlet`에 전달
2. 요청한 url에 맞는 `controller` 검색하여 `Handler Mapping`에 전달
3. `HandlerMapping`에서 해당 `controller`에 처리 요청
4. `controller`에서 처리 결과를 `Handler Adapter`에서 ModelAndView 객체로 변환하여 `Dispatcher Servlet`에 전달
5. `Dispatcher Servlet`에서 전달받은 ModelAndView 객체를 이용하여 매핑되는 View를 검색
6. `viewResolver`에서 처리 결과를 `view`에 전달
7. 처리결과가 포함된 `view`를 `Dispatcher Servlet`에 전달
8. `Dispatcher Servlet`에서 최종 응답 결과를 클라이언트에게 반환

<br>

- DispatcherServlet : 클라이언트의 요청을 전달 받아 요청에 맞는 컨트롤러가 반환한 결과값을 View에 전달하여 알맞은 응답 생성
- HandlerMapping : 클라이언트의 요청 URL을 어떤 컨트롤러가 처리할지 결정
- Controller : 클라이언트의 요청을 처리한 뒤, 결과를 DispatcherServlet에 반환
- ModelAndView : 컨트롤러가 처리한 결과 정보 및 뷰 선택에 필요한 정보를 담음
- ViewResolver : 컨트롤러의 처리 결과를 생성할 뷰를 결정
- View : 컨트롤러의 처리 결과 화면을 생성, JSP 또는 템플릿 엔진을 뷰로 사용
<br><br><br><br><br>

참고 자료: <br>
[https://velog.io/@ejung803/Spring-Web-MVC의-Dispatcher-Servlet의-동작-원리](https://velog.io/@ejung803/Spring-Web-MVC%EC%9D%98-Dispatcher-Servlet%EC%9D%98-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC)

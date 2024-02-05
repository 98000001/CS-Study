## **ApplicationContext**

- 스프링 컨테이너
- `BeanFactory` 인터페이스의 하위 인터페이스로 부가 기능을 추가한 것 (`BeanFactory`는 스프링 컨테이너의 최상위 인터페이스 (스프링 빈을 관리하고 조회하는 역할))
- `ApplicationContext`는 `BeanFactory` + 부가 기능(국제화 기능, 환경 변수 관련 처리, 애플리케이션 이벤트, 리소스 조회)
- 스프링 컨테이너 내부에는 **빈 저장소**가 존재. 빈 저장소는 key로 빈 이름을 가지고 있으며, value로 실제 빈 객체를 가지고 있음
- 스프링 컨테이너는 기본적으로 빈을 **싱글톤**으로 관리 (싱글톤 컨테이너)

<br>

### 빈(Bean) 요청 시 처리 과정

클라이언트에서 해당 빈을 요청하면 애플리케이션 컨텍스트는 다음과 같은 과정을 거쳐 빈을 반환

<img src="https://github.com/98000001/CS-Study/assets/80199502/8203071e-8733-4546-bc13-cb237ede4965"  width="800">

- ApplicationContext는 @Configuration이 붙은 클래스들을 설정 정보로 등록해두고, @Bean이 붙은 메소드의 이름으로 빈 목록을 생성
- 클라이언트가 해당 빈을 요청
- ApplicationContext는 자신의 빈 목록에서 요청한 이름이 있는지 찾음
- ApplicationContext는 설정 클래스로부터 빈 생성을 요청하고, 생성된 빈을 돌려줌

<br>

### 애플리케이션 컨텍스트 장점

- 클라이언트는 @Configuration이 붙은 구체적인 팩토리 클래스를 알 필요가 없음
- 애플리케이션 컨텍스트는 종합 IoC 서비스를 제공
- 애플리케이션 컨텍스트를 통해 다양한 빈 검색 방법을 제공

<br><br><br><br><br>

참고 자료:<br>
https://mangkyu.tistory.com/151

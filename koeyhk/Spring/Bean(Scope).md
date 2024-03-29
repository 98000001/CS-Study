# Spring Bean

- **Spring IoC 컨테이너가 관리하는 자바 객체**
- 스프링 빈(Bean) 사용이유
    - 스프링 간 객체가 의존관계를 관리하도록 하는 것

### Spring Bean의 생명 주기

- `객체 생성 -> 의존 설정 -> 초기화 -> 사용 -> 소멸`의 생명 주기
- Bean은 스프링 컨테이너에 의해 생명주기를 관리
- 스프링 컨테이너가 초기화될 때 먼저 빈 객체를 설정에 맞춰 생성하며 의존 관계를 설정한 뒤 해당 프로세스가 완료되면 빈 객체가 지정한 메소드를 호출해서 초기화를 진행
- 빈 초기화 방법에는 **@PostConstruct**와 빈 소멸에서는 **@PreDestory**를 사용

### **스프링 빈(Bean) 등록 방법**

- xml에 직접 등록
- @Bean 어노테이션 이용
- 컴포넌트 스캔 (@Component, @Controller, @Service, @Repository) 어노테이션 이용

<br>

## Bean Scope

- 빈이 존재할 수 있는 범위
- 스프링은 빈이라는 개념으로 객체를 만들고 기본적으로 싱글톤화시켜 관리해줌
- 스프링 컨테이너는 빈 객체의 스코프(scope)를 설정하여 빈 객체의 생명 주기를 제어
- 빈으로 생성된 객체들은 스프링 컨테이너와 함께 시작되어서 종료될 때까지 스프링이 관리해주는데 이 이유는 스프링 빈들은 싱글톤 스코프로 관리되기 때문

### 스프링이 가지는 스코프

- 싱글톤: 기본 스코프, 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프
- 프로토타입: 스프링 컨테이너는 프로토타입 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 매우 짧은 범위의 스코프 (빈 콜백 중 `@PreDestroy`와 같은 종료메서드가 호출이 안됨)
- 웹 관련 스코프
    - request: 웹 요청이 들어오고 나갈때 까지 유지되는 스코프
    - session: 웹 세션이 생성되고 종료될 때 까지 유지되는 스코프
    - application: 웹의 서블릿 컨텍스와 같은 범위로 유지되는 스코프
 

<br><br><br><br><br>

참고 자료: <br>
https://chung-develop.tistory.com/56 <br>
https://developer-ellen.tistory.com/198

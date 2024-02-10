# Bean(Scope)

### Bean

- 스프링이 시작될 때 함께 생성되고, 스프링 컨테이너가 종료될 때까지 유지되는 것
- Spring IoC 컨테이너에 의해 인스턴스화, 관리, 생성됨
- Spring에서 관리하는 POJO 객체
- Spring IoC 컨테이너가 관리하는 자바 객체

## Spring Bean Scope

Bean 이 존재할 수 있는 범위

### Singleton

- 디폴트 값. 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프
- Spring 컨테이너에서 한번 생성
- Bean 마다 하나의 객체 생성.
    - 스프링을 통해 Bean 을 제공받으면 동일한 객체라는 가정 하에 개발

### Prototype

- 스프링 컨테이너는 Prototype Bean의 생성과 의존 관계 주입까지만 관여하고 더 이상은 관리하지 않음
    - 따라서 @PreDestory 같은 종료 메소드 호출 되지 않음
- Prototype Bean 조회하면 스프링 컨테이너는 항상 새로운 인스턴스 생성해 반환
    - 하나의 Bean 정의에 대해 다수의 객체 존재 가능.
- Prototype Bean 요청 → 컨테이너는 Prototype Bean 생성, 필요한 의존관계 주입 → Prototype Bean은 스프링 컨테이너에서 Bean 조회할 때 생성되고 초기화 메소드도 실행 → Prototype Bean 이기에 클라이언트에게 Bean 반환 이후에는 생성한 Prototype Bean 관리하지 않음. → @PreDestroy 같은 종료 콜백 메소드 호출되지 않음

### Singleton 과 Prototype Bean 을 함께 사용하려면?

1. Singleton Bean 을 조회하면 스프링 컨테이너는 항상 같은 인스턴스 반환. Prototype Bean은 항상 새로운 인스턴스를 생성해 반환. 
2. Singleton Bean이 Prototype Bean을 주입받는다면 Singleton Bean이 생성되고, 의존 관계 주입 시점에만 Prototype Bean이 조회. 이후에는 계속 같은 빈이 사용됨.
3. 호출시마다 새로운 객체가 필요해 Prototype Bean으로 주입했는데 개발자의 의도대로 되지 않음
4. 따라서 **Prototype Bean 을 주입 시점에만 새로 생성하는 것이 아니라, 사용할 때마다 새로 생성해서 사용해야함.**
5. 이를 해결하기 위한 가장 간단한 방법은. **Prototype Bean 의존 관계를 주입받는 것이 아니라. ApplicationContext에 매번 Bean을 요청하는 것.** 
    1. 하지만 이렇게 되면 스프링에 종속적인 코드가 되고 단위 테스트가 어려워짐 → objectprovider

### ObjectProvider

- 스프링 ApplicationContext 전체를 주입받는 대신, ObjectProvider를 주입받아 사용.
- 의존 관계를 외부에서 주입 받는것이 아니라, *직접 필요한 의존관계를 찾는 것* DL (Dependency Lookup) , 의존관계 조회.
    - 지정한 빈을 컨테이너에서 대신 찾아주는 DL(Dependency Lookup)
- getObject() 호출시 스프링 컨테이너를 통해 해당 빈을 찾아 반환
- 스프링이 제공하는 기능을 사용하지만 기능이 단순해 단위 테스트를 만들거나 mock 코드 만들기는 쉬움

## 웹 스코프

웹 환경에서 동작, 스프링이 해당 스코프 종료 시점까지 관리. 종료 메소드 호출

- request
    - HTTP 요청 하나 입출입까지 유지되는 스코프
    - 각 HTTP 요청마다 별도의 빈 인스턴스가 생성되고 관리됨
- session
    - HTTP Session과 동일한 생명주기를 가지는 스코프
- application
    - Servlet Context와 같은 범위로 유지되는 스코프
- Singleton Bean 은 스프링 컨테이너 생성 시 함께 생성되어 라이프 사이클을 같이 하지만, 웹 스코프는 HTTP 요청이 올 때 새로 생성되고 응답하면 사라지기 때문에, Singleton Bean 생성 시점에는 아직 생성되지 않음. 따라서 의존관계 주입 불가 → proxy

### Spring Bean의 생명주기

- `객체 생성 → 의존 설정 → 초기화 → 사용 → 소멸`
- Bean은 스프링 컨테이너에 의해 생명주기를 관리
- 빈 초기화방법은 @PostConstruct를 빈 소멸에서는 @PreDestroy를 사용
- 생성한 스프링 빈을 등록할 때는 ComponentScan을 이용하거나 @Configuration 의 @Bean 을 사용하여 Bean 설정파일에 직접 Bean을 등록

### Spring에서 Singleton 을 사용하는 이유

Application Context 에 의해 등록되는 Bean은 기본적으로 Singleton으로 관리됨

여러번 Bean을 요청해도 매번 동일한 객체를 돌려줌

Singleton 으로 Bean을 관리하는 이유는 대규모 트래픽을 처리할 수 있도록 하기 위해

Bean을 Singleton Scope로 관리해 1개의 요청이 왔을 때 여러 스레드가 Bean을 공유해 처리하도록 함.
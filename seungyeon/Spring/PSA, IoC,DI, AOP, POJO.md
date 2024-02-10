# PSA, IoC/DI, AOP, POJO(각각에 대한 내용과 도입 이유)

## POJO(Plain Old Java Object)

오래된 방식의 간단한 자바 오브젝트

EJB 등에서 사용되는 Java Bean 이 아닌, Getter와 Setter로 구성된 가장 순수한 형태의 기본 클래스

옛날 순수한 객체지향성이 컸던 시절로 돌아가자는 취지로 POJO

### POJO Framework

POJO의 장점 + EJB의 장점 = Hibernate, Spring

### 하이버네이트

persistence 기술과 object-related DB mapping 을 순수한 POJO를 이용해 사용할 수 있게 만듬

- 하이버네이트가 사용하는 POJO 엔티티들은 객체지향적인 다양한 설계, 구현이 가능
- 특정 기술에 종속적이면 POJO가 아닌데, 스프링에서 ORM을 위한 표준 인터페이스 JPA를 정함. 이에 따라 ORM 을 사용할 수 있도록 함.
    
    → 스프링이 엔터프라이즈 기술을 도입하며 POJO를 유지하는 방법 → PSA
    

### POJO의 기준

1. 객체지향적으로 설계 되었는가?
    - 반복적인 템플릿 코드가 없음
    - 테스트하기 쉬움
    - 확장 및 재활용이 쉬움
2. 테스트가 용이한가?
    
    자동화된 테스트 코드 작성
    
     
    

## PSA(Portable Service Abstraction)

환경의 변화와 관계없이 일관된 방식의 기술로 접근 환경을 제공하는 추상화 구조

- **특정 클래스가 추상화된 상위 클래스를 일관되게 바라보며 하위 클래스의 기능을 사용**
- 기존 작성된 코드를 수정하지 않으면서 확장 가능.
- Spring의 라이브러리들은 *POJO 원칙을 지키기 위해 PSA 형태의 추상화.*
- Spring Web MVC, Spring Data, Spring Transaction 등 다양한 PSA 제공
    - Spring Web MVC
        - 일반 클래스에 @Controller 어노테이션을 사용하면 요청을 매핑할 클래스가 됨.
        - 그 클래스에선 @GetMapping, @PostMapping 어노테이션을 이용해 매핑할 수 있음
        - 서블릿을 low level로 개발하지 않아도 서블릿을 간편하게 개발할 수 있음
            - HttpServlet을 상속 받아 doGet(), doPost()를 구현하는 등의 작업을 하지 않아도 됨
        - spring-boot-starter-web 의존성 대신 spring-boot-starter-webflux 를 사용하면 Tomcat 기반이 아닌 netty 기반으로 실행 가능
    - Spring Transaction
    
    ![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b790a1db-0cff-45f3-bfb4-ff5f3db49559/3dcff04d-8b53-4cc8-8449-7954a41e7d01/Untitled.png)
    
    - Spring 의 @Transactional은 최상위 PlatformTransactionManager를 이용하고 필요한 TransactionManager를 DI로 주입받아 사용
- 어노테이션과 뒷단의 여러가지 복잡한 인터페이스, 기술들을 기반으로 사용자가 코드를 거의 변경하지 않고 웹 기술 스택을 간편하게 바꿀 수 있도록 함
- **PSA를 통해 애플리케이션의 요구 사항 변경에 유연하게 대처할 수 있음**

### 서비스 추상화(Service Abstraction)

- 일관된 방식으로 서비스 기능 사용
- 클라이언트 클래스는 구현체 객체를 생성하여 인터페이스 타입의 변수에 할당한다(업 캐스팅)
- 이후 생성자로 인터페이스 객체를 전달한다 (의존성 주입)

## AOP(Aspect - Oriented Programming)

OOP를 돕는 보조적인 기술로, 관심사의 분리(기능의 분리) 를 해결하기 위해 만들어진 프로그래밍 패러다임

- 핵심 관심 사항(Core-Conern)과 공통 관심 사항(Cross-Cutting Concern) 으로 분리 및 모듈화
    - 핵심 기능 Core Concern : 업무 로직
    - 부가 기능 Cross-Cutting Concern : 핵심 기능을 도와 주는 부가적인 기능
- OOP를 적용해도 핵심 기능과 부가기능을 쉽게 분리된 모듈로 작성하기 어려운 점을 AOP가 해결
- AOP는 부가 기능을 Aspect로 정의, 핵심 기능에서 부가기능을 분리하여 **핵심 기능을 설계, 구현할 때 객체 지향적 가치를 지킬 수 있게 도와줌**
- 즉, 필수적이지만 어쩔 수 없이 반복되는 코드를 리팩토링 할 수 있도록. 여러곳에서 사용될만한 코드들이 한곳에서 유지되고 관리됨.

- 프록시 패턴 기반
    - Spring은 target 객체에 대한 proxy 만들어 제공
    - target 을 감싸는 프록시는 실행 시간에 생성
    - proxy는 advice를 target 객체에 적용하며 생성되는 객체
    - proxy를 쓰는 이유는 접근 제어 및 부가기능 추가 하기 위해
- 프록시가 호출을 가로챔(Intercept)
    - 전처리 advice : target 객체에 대한 호출을 가로채 Advice의 부가 기능 로직을 수행한 후 target의 핵심 기능 로직 호출
    - 후처리 advice : target의 핵심 기능 로직 메소드를 호출한 후 부가기능 수행
- 메소드 JoinPoint 만 지원
    - 동적프록시 기반으로 AOP 구현, 메소드 조인 포인트만 지원
    - 핵심 기능 target의 메소드가 호출되는 런타임 시점에만 부가기능 적용 가능
    - AseptJ 같은 고급 AOP 사용하면 객체의 생성, 필드값의 조회와 조작, static 메소드 호출 및 동기화 등의 다양한 작업에 부가기능 적용 가능

### AOP 용어

- Target
    - 부가기능을 부여할 대상
        - 핵심기능을 담고 있는 모듈
- Aspect ( = Advice + PointCut )
    - 부가 기능 모듈
        - 핵심 기능에 부가되어 의미를 갖는 모듈
    - 부가될 기능을 정의한 Advice와 Advice를 어디에 적용할지를 결정하는 PointCut을 함께 갖고있음
    - 애플리케이션의 핵심적인 기능에서, 부가적인 기능을 분리해 Aspect라는 모듈로 만들어 설계하고 개발하는 방법
- Advice
    - 실질적으로 부가기능을 담은 구현체
    - Target 오브젝트에 종속되지 않기때문에 부가기능에만 집중할 수 있음
    - Aspect가 무엇을 언제 할지 정의
- PointCut
    - 부가기능이 적용될 대상을 선정하는 방법
    - Advice를 적용할 JoinPoint를 선별하는 기능을 정의한 모듈
- JointPoint
    - Advice가 적용될 수 있는 위치
    - Spring에서는 메소드 조인포인트만 제공
    - Target 객체가 구현한 모든 메소드는 JointPoint가 됨
- Proxy
    - Target을 감싸서 Target의 요청을 대신 받아주는 랩핑 오브젝트
    - 클라이언트에서 Target을 호출하면 !Target인 Target을 랩핑하고 있는 Proxy가 호출되어 Target 메소드 실행 전에 선처리, 후처리 실행
- Introduction
    - Target 클래스에 코드 변경 없이 신규 메소드나 멤버 변수를 추가하는 기능
- Weaving
    - 지정된 객체에 Aspect를 적용해 새로운 프록시 객체를 생성하는 과정
    - Spring AOP는 런타임에서 프록시 객체 생성

## IoC/DI

### IoC (Inversion of Control)

객체의 생성, 생명주기 관리까지 모든 객체에 대한 제어권이 바뀌었다는 것을 의미

컴포넌트 의존관계 설정, 설정 및 생명주기 해결위한 디자인 패턴

### IoC 컨테이너

- 컨테이너는 보통 객체의 생명주기 관리, 생성된 인스턴스들에게 추가 기능 제공 하는 것.
- 스프링도 객체를 생성,관리,의존성 관리해주는 컨테이너가 있는데, IoC 컨테이너.
- 인스턴스 생성부터 소멸까지 인스턴스 생명 주기를 컨테이너가 대신 해줌
    - 객체의 생성, 의존성 관리 책임
    - POJO의 생성, 초기화, 서비스 , 소멸에 대한 권한
    - 개발자들이 POJO 직접 생성할 수있지만 컨테이너에 맡김
    - 개발자는 비즈니스 로직에 집중
    - 객체 생성 코드가 없어 TDD에 용이
- DL (Dependency Lookup)
    - 저장소에 저장되어있는 Bean 에 접근하기 위해 컨테이너가 제공하는 API로 Bean을 Lockup
    - 컨테이너 종속이 증가
- DI (Dependency Injection)
    - 각 클래스간 의존 관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결
    - 의존성 주입 ; 필요한 객체를 직접 생성하는 것이 아닌 외부로부터 객체를 받아서 사용하는 것
        - 객체간 결합도 줄이고, 의존성 줄이고 코드의 재활용성 높일 수 있음
        - test 가 용이해짐
    - Field Injection
        - 필드에 @Autowired
            - 코드가 간결하지만 외부에서 변경하기 힘듦
            - 프레임워크에 의존적이고 객체지향적으로 좋지 않음
    - Setter Injection
        - Setter 메소드에 @Autowired
        - 수정자 주입은 set 메소드를 public 으로 열어두어야하기에 언제 어디서든 변경 가능하기에 안좋음
    - **Constructor Injection (Best!)**
        - 클래스 생성자가 하나이고 그 생성자로 주입받을 객체가 빈으로 등록되어있을 때.
        - 생성자 주입을 권장하는 이유
            - 순환 참조 방지
                - 필드 주입과 수정자 주입은 빈이 생성된 후 참조하기에 애플리케이션이 아무 오류, 경고 없이 구동 → 실제 코드가 호출될 때까지 문제를 알 수 없음
                - 생성자를 통해 주입하고 실생하면 BeanCurrecntlyInCreationException 발생
            - 불변성
                - 생성자로 의존성 주입시 final 선언할 수 있고 이를 통해 런타임에서 의존성 주입받은 객체가 변할 일이 없어짐. 하지만 수정자, 필드 주입시 불필요한 수정 가능성을 열어두게 되고, OCP를 위반.
                - 변경 가능성 배제, 불변성 보장
                - 필드 주입은 null 이 될 가능성이 있는데 final로 선언한 생성자 주입은 null이 불가능
            - 테스트에 용이함
                - 독립적 인스턴스가 가능한 POJO를 사용하면 DI 컨테이너 없이도 의존성 주입해 사용 가능
                - 코드의 가독성이 높아지며 유지보수에 용이
- 스프링 컨테이너 (IoC 컨테이너)가 관리하는 객체를 Bean, 이 빈들을 관리한다는 의미로 BeanFactory 라고 부름.
    - 자바 어플리케이션은 어플리케이션 동작을 제공하는 객체로 이루어짐. 이때 객체들은 독립적으로 동작하기보다 서로 상호 작용하여 동작함. 이렇게 상호작용하는 객체를 ‘객체 의존성’ 이라고함
    - 스프링에서는 스프링 컨테이너에 객체끼리 의존성 주입(DI) 하는 역할을 해주는데 이 스프링 컨테이너에 등록한 객체들이 Bean
    - 객체의 생성과 객체 사이 런타임 관계를 DI 관점에서 볼 때 BeanFactory
- BeanFactory + 여러가지 컨테이너 기능 = Application Context
    - BeanFactory
        - BeanFactory 계열만 구현한 클래스는 단순히 컨테이너에서 객체를 생성하고 DI 처리하는 기능만 제공. 보통은 BeanFactory를 바로 사용하지 않고 ApplicationContext 사용
        - Bean을 등록,생성,조회,관리
        - 팩토리 디자인 패턴을 구현한 것으로 BeanFactory는 빈을 생성하고 분배하는 책임을 가짐
        - Bean을 조회할 수 있는 getBean()
    - ApplicationContext
        - Bean을 등록,생성,조회,관리
        - 스프링의 각종 부가 기능 추가로 제공
            - 국제화 텍스트 메시지 관리
            - 이미지같은 파일 자원 로드 관리
            - **리스너로 등록된 빈에게 이벤트 발생 알림**
- 스프링 컨테이너에 Bean 등록하는 방법
    - 컴포넌트 스캔과 자동 의존관계 설정
        - 클래스 선언부 위에 @Component 어노테이션
            - @Controller, @Service, @Repository 는 모두 @Component를 포함함
    - 자바 코드로 직접 스프링 빈 등록
        - 설정 클래스 만들고 @Configuration 어노테이션을 클래스 선언부에 추가
        - 특정 타입을 리턴하는 메소드를 만들고 @Bean 어노테이션 붙여주면 자동으로 해당 타입 빈 객체 생성
            - @Bean
                - @Configuration 설정된 클래스 메소드에서 사용 가능
                - 메소드 리턴 객체가 스프링 Bean 객체임을 선언
                - Bean 이름은 기본적으로 메소드 이름. 이름 변경 가능
                - @Scope를 통해 객체 생성 조정 가능
                - @Component 어노테이션으로 @Configuration 없이도 빈 객체 생성 가능
                - 빈 객체에 init(), destroy() 등 라이프사이클 메소드 추가해 @Bean 에서 지정 가능
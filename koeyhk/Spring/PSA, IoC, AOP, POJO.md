## POJO (Plain Old Java Object)

<img src="https://github.com/98000001/CS-Study/assets/80199502/7dd128b2-18c9-4c54-8f6b-89d4c3f4b3ba"  width="300">

- POJO는 IoC/DI, AOP, PSA를 통해서 달성할 수 있음
- Java로 생성하는 순수한 객체를 뜻함
- POJO는 객체 지향적인 원리에 충실하면서 환경과 기술에 종속되지 않고, 필요에 따라 재활용될 수 있는 방식으로 설계된 객체

### **POJO 프로그래밍**

POJO에 애플리케이션의 핵심 로직과 기능을 담아 설계하고 개발하는 방법

1. Java나 Java의 스펙에 정의된 것 이외에는 다른 기술이나 규약에 얽매이지 않아야 함
2. 특정 환경에 종속적이지 않아야 함 (환경에 독립적)

### POJO 프로그래밍 필요한 이유

- 특정 기술에 종속적이지 않고, 재사용 가능, 유연한 확장
- 코드가 간결해짐, 디버깅이 쉬워짐, 테스트가 단순해짐
- **객체지향적인 설계를 제한없이 적용 가능**

<br>

## **IOC/DI**

<img src="https://github.com/98000001/CS-Study/assets/80199502/87e0ae27-1985-43d3-a650-e827c57da58b"  width="600">


### IOC **(Inversion of Control)**

**개발자가 제어해야할 요소들을 Spring Framework에서 대신 제어해주는 것**

- 컨트롤의 제어권이 개발자가 아니라 프레임워크에 있음
- 객체의 생성부터 모든 생명주기의 관리까지 객체의 제어권이 바뀐 것을 의미
- Libraray는 개발자가 애플리케이션의 흐름을 주도하고 Framewrok는 애플리케이션이 애플리케이션의 흐름을 주도하는것으로 주도권이 뒤바뀐 것을 바로 IoC(Inversion of Control)
- 장점
    - 의존성을 역전시켜 객체 간의 결합도를 줄이고 유연한 코드를 작성할 수 있음 → 코드의 재사용성이 좋아지고, 유지 보수가 편해짐
    - Spring Container(IoC Container)가 Bean을 관리해주므로 개발자는 객체 관리 대신 다른 부분에 더 집중할 수 있음

### DI **(Dependency Injection)**

- 객체간의 의존관계를 관리하는 기술
- 어떤 객체에 스프링 컨테이너가 또 다른 객체와 의존성을 맺어주는데, 이는 사용자가 객체를 직접 생성하는 게 아니라 외부에서 생성한 후 주입시켜 주는 것을 의미
- 장점
    - 객체 간의 결합도, 의존성이 줄어듦 (의존 관계를 분리하게 되면 주입받는 대상이 수정되어도 수정할 필요가 없어지거나 줄어듦)
    - 코드의 재활용성이 높아지고 가독성이 높아짐
    - Unit Test가 용이해짐 (테스트하기 좋은 코드)
- 스프링에서는 스프링 컨테이너 ApplicationContext를 이용하여 설정 정보를 생성, 등록하고 필요한 객체를 생성자 혹은 setter를 통해 주입

### 의존성 주입 방법

- **생성자 주입**
    - 생성자를 통해서 의존 관계를 주입받는 방법
    - 생성자에 @Autowired를 하면 스프링 컨테이너에 @Component로 등록된 빈에서 생성자에 필요한 빈들을 주입
    - 생성자 호출 시점에 **1번만 호출되는 것을 보장**
- **수정자 주입 (setter 주입)**
    - setter라 불리는 필드의 값을 변경하는 수정자 메서드를 통해서 의존 관계를 주입하는 방법
    - @Component를 통해 실행하는 클래스를 스프링 빈으로 등록하고 의존관계를 주입, @Autowired가 있는 수정자들을 자동으로 의존관계를 주입
    - 선택과 변경 가능성이 있는 의존 관계에 사용, @Autowired를 입력하지 않으면 실행이 되지 않음
- **필드 주입**
    - 필드에 @Autowired를 붙여서 바로 주입하는 방법
    - 외부에서 변경이 불가능하여 테스트하기 어려운 단점
- **일반 메서드 주입**

<br>

## AOP **(Aspect Oriented Programming)**

<img src="https://github.com/98000001/CS-Study/assets/80199502/60dbba9d-b0b7-4f9c-8efe-d91784aa3442"  width="600">

- **관점 지향 프로그래밍**
- 핵심 로직과 부가 기능을 분리하여 애플리케이션 전체에 걸쳐 사용되는 부가 기능을 모듈화하여 재사용할 수 있도록 지원하는 것
    - 핵심 관심 사항 : 애플리케이션의 목적 달성을 위한 핵심 로직 (비즈니스 로직)
    - 공통 관심 사항(부가 기능) : 애플리케이션 전반에 걸쳐 공통적으로 사용되는 기능
- 여러 개의 클래스에서 반복해서 사용하는 코드가 있다면 해당 코드를 모듈화 하여 공통 관심사로 분리 (공통된 기능을 재사용하는 기법)
- **코드의 간결성 유지, 객체 지향 설계 원칙에 맞는 코드 구현, 코드의 재사용**
- 장점
    - 애플리케이션 전체에 흩어진 공통 기능이 하나의 장소에서 관리되어 유지보수가 좋음
    - 핵심 로직과 부가 기능의 명확한 분리로, 핵심 로직은 자신의 목적 외에 사항들에는 신경쓰지 않음

<br>

## **PSA(Portable Service Abstraction)**

- 환경의 변화와 관계없이 일관된 방식의 기술로의 접근 환경을 제공하는 추상화 구조
- 특정 클래스가 추상화된 상위 클래스를 일관되게 바라보며 하위 클래스의 기능을 사용하는 것
- PSA가 적용된 코드는 개발자의 기존에 작성된 코드를 수정하지 않으면서 확장할 수 있으며, 어느 특정 기술에 특화되어 있지 않는 코드
- 일관된 방식으로 해당 서비스의 기능을 사용할 수 있음
- 애플리케이션에서 특정 서비스를 이용할 때, 서비스의 기능을 접근하는 방식 자체를 일관되게 유지하면서 기술 자체를 유연하게 사용할 수 있도록 하는 것을 PSA(일관된 서비스 추상화)



<br><br><br><br><br><br>

참고 자료: <br>
https://bestinu.tistory.com/47 <br>
[https://velog.io/@backtony/Spring-AOP-총정리](https://velog.io/@backtony/Spring-AOP-%EC%B4%9D%EC%A0%95%EB%A6%AC) <br>
https://ittrue.tistory.com/214

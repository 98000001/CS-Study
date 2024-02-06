## POJO(Plain Old Java Object)
PO는 순수 자바로 생성하는 객체
JO는 객체와 객체가 관계를 맺을 수 밖에 없는 객체지향 프로그래밍
특정 프레임워크나 라이브러리에 의존하지 않는 순수한 자바 객체
스프링은 이러한 POJO들을 사용하여 애플리케이션을 구성하고 관리하는데 중점을 둠

### POJO 프로그래밍 필요한 이유
특정 기술에 종속적이지 않고, 재사용 가능, 유연한 확장
코드가 간결해짐, 디버깅이 쉬워짐, 테스트가 단순해짐
객체지향적인 설계를 제한없이 적용할 수 있습니다.

## IOC(Inversion of Control)(+DI(Dependency Injection))
스프링 애플리케이션에서는 오브젝트(빈)의 생성과 의존 관계 설정, 사용, 제거 등의 작업을 애플리케이션 코드 대신 스프링 컨테이너가 담당
스프링 컨테이너가 코드 대신 오브젝트에 대한 제어권을 가지고 있음

#### IoC 컨테이너
IoC를 담당하는 컨테이너 => 빈 팩토리(Spring container에 대한 기본적인 API 정의), DI 컨테이너, 애플리케이션 컨텍스트(기본적인 bean 관리 외에, annotation 기반 설정, 메시지 및 이벤트 처리, 국제화, 트랜잭션 처리 등 다양한 부가 기능 제공)

<img width="393" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/cf3ff0b1-4f6f-4f4e-8bdb-4130ad51ae97">


#### DI(Dependency Injection)
객체간의 의존(한 객체가 다른 객체의 메서드를 사용)을 의미
다른 클래스의 기능을 사용 할 때, 다른 클래스에 의존한다

###### 느슨한 결합
테스트, 디버깅, 유지보수 등을 원활히 하기 위해서 객체간의 의존도를 낮추어야함
클래스 내부에서 new연산으로 객체를 생성하면 강한게 결합이 되니 외부에서 따로 만든 객체를 사용하는 객체에 외부에서 주입시켜 느슨하게 결합되도록
##### Spring 컨테이너에 클래스를 넣어 Spring 컨테이너가 알아서 객체를 생성하고 의존성 객체를 주입 하도록 하는 기능

1. 생성자 방식(constructor-based injection)
– Bean의 생성자(constructor)를 통해 의존 객체를 주입 – 이용가능한 생성자가 bean 클래스에 정의되어야 함
2. Setter method 방식 (setter-based injection)
– Property에 대한 setter method를 통해 의존 객체 주입
– Bean class에 property에 대한 setter method가 정의되어 있어야 함

생성자 방식
– Bean 객체를 생성하는 시점에 모든 의존 객체가 주입됨
– 성능상 유리하고, 객체를 사용하기 전에 필요한 의존 객체가 모두 주입된 상태이므로 NullPointerException 발생 가능성 낮음 
– 생성자의 인자들의 순서대로 적합한 의존 객체를 전달해야 함
   인자가 많을 경우 어떤 필드에 어떤 의존 객체를 주입하는지 파악하기 어려움

Setter method 방식 
– 생성자를 통해 bean 객체가 생성된 후 의존 객체가 주입됨
– setter method를 통해 각 필드마다 필요한 의존 객체를 주입하므로 설정이 명확하고 용이함
– setter들을 별도로 실행하므로 성능이 다소 저하되고, setter의 실행이 누락된 경우 해당 객체 참조 시 NullPointerException 발생 가능


## AOP(Aspect Oriented Programming)

# Spring vs Spring Boot

### Spring Framework

Java 기반 오픈소스 BackEnd 프레임 워크

개발자에게 겨울은 끝나고 봄이 왔다

- 경량 컨테이너
- IoC
    - 컨트롤 제어권이 개발자에게 있는 것이 아닌 프레임워크에 있음
    - Servlet , Bean 같은 코드를 개발자가 작성하지 않고 프레임워크가 대신 수행
    - 객체 생성, 의존 관계 설정 등을 프레임워크가 대신 해줌
- DI
    - Spring Framework에 의존성을 주입하면서 객체 간 결합을 느슨하게 함
    - 객체간 결합이 느슨하면 코드의 재사용성이 증가하고 단위 테스트가 용이해짐
- AOP
    - 핵심 기능을 제외한 부수적인 기능을 프레임워크가 제공
    - 예를들어 Spring 프로젝트에 security 를 적용하거나 logging 을 추가할 때 기존 비즈니스 로직을 건들지 않고 AOP로 추가 가능

### Spring Boot

스프링 프레임워크를 사용하기 위한 설정의 많은 부분을 자동화 하여 사용자가 편하게 스프링을 활용할 수 있도록 도움

Spring Boot starter 만 추가해주면 바로 API를 정의하고 내장된 tomcat 으로 웹 애플리케이션 서버를 실행할 수 있음.

### Spring Boot starter

- 특정 목적을 달성하기 위한 의존성 그룹
- 만약 JPA가 필요하다면 spring-boot-starter-data-jpa 만 추가하면 Spring Boot가 그에 필요한 라이브러리들을 알아서 받아옴

### Spring vs Spring boot

- Dependency
    - Spring Framework 는 dependency 설정 시 모든 버전관리를 따로 해줘야함.
    - Spring Boot 는 starter 가 대부분의 dependency 버전 호환 관리를 해줌.
- Configuration
    - Spring Framework는 configuration 설정을 할 때 모든 어노테이션 및 빈 등록 등을 설정해야함
    - Spring Boot는 AutoConfiguration이 있음. @SpringBootApplication 덕분에 많은 외부 라이브러리, 내장 톰캣 서버 등이 실행될 수 있음
        - Embeded tomcat 을 사용하기에 따로 tomcat 을 설치하거나 매번 버전 관리하는 수고로움을 덜어줌
            - Spring Boot 내부에 tomcat 포함
        - @SpringBootApplication
            - @ComponentScan
                - @Component, @Controller, @Repository 등의 어노테이션이 붙어 있는 객체들을 스캔해 자동으로 Bean 등록
            - @EnableAutoConfiguration
                - @ComponentScan 이후 사전에 정의한 라이브러리들을 Bean 에 등록.
- 편리한 배포
    - Spring Framework는 war 파일을 WAS에 담아 배포
    - Spring Boot는 내장 tomcat WAS가 있어 jar 파일로 간편하게 배포 가능
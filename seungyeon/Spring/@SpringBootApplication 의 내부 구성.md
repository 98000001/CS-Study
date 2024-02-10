# @SpringBootApplication의 내부 구성

### @SpringBootApplication

auto-configuration 을 담당

Spring Boot 시작 시 필요한 것들을 자동으로 구성하고 Bean 을 생성하는 등 기본적인 설정을 포함하고 있음

```java
@Target({ElementType.TYPE})
@Retention(RetentionPolicy.RUNTIME)
@Documented
@Inherited
**@SpringBootConfiguration**
**@EnableAutoConfiguration**
**@ComponentScan(**
    excludeFilters = {@Filter(
    type = FilterType.CUSTOM,
    classes = {TypeExcludeFilter.class}
), @Filter(
    type = FilterType.CUSTOM,
    classes = {AutoConfigurationExcludeFilter.class}
)}
)
public @interface SpringBootApplication {
```

### @EnableAutoConfiguration

우리가 필요할 것 같은 빈들을 자동으로 설정해주는 기능을 활성화

- 미리 정의 되어있는 Bean 또는 @Configuration에 등록된 Bean들을 가져와 스프링 컨테이너에 추가
    - spring-boot-autoconfigure > META-INF > spring.facotries 에 위치

### @ComponentScan

현재 패키지 이하에서 @Component, @Configuration, @Repository, @Service, @Controller, @RestController 등의 어노테이션이 붙어있는 클래스를 찾아 Bean 으로 등록

### @SpringBootConfiguration

SpringBoot의 설정을 나타내는 어노테이션. 프로젝트당 한번
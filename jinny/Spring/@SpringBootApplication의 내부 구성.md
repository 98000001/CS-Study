## @SpringBootApplication의 내부 구성
@SpringBootApplication
- @EnableAutoConfiguration
- @ComponentScan
- @SpringBootConfiguration

@EnableAutoConfiguration – 설정 자동 등록하기
@EnableAutoConfiguration은 Spring boot의 핵심으로써, 미리 정의되어 있는 Bean들을 가져와서 등록

@ComponentScan – 빈 등록하기
@ComponentScan은 현재 패키지 이하에서 아래와 같은 어노테이션이 붙어 있는 클래스들을 찾아서 빈으로 등록하는 역할
(@Component@Configuration@Repository@Service@Controller@RestController)

@SpringBootConfiguration - @Configuration의 용도
@Configuration은 spring 에 빈 팩토리를 위한 오브젝트를 설정을 담당하는 클래스라고 인식 할 수 있도록 알려주는 어노테이션

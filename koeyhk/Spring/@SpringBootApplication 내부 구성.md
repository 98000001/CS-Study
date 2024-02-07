## @SpringBootApplication 내부 구성

### @SpringBootConfiguration

- @Configuration의 하위 어노테이션으로 @Configuration과 동일한 역할을 수행
- Spring에 빈 팩토리를 위한 오브젝트를 설정을 담당하는 클래스라고 인식 할 수 있도록 알려주는 어노테이션

### @EnableAutoConfiguration

- 필요할 것 같은 빈들을 자동으로 설정해주는 자동 설정 기능을 활성화
- 정의되어 있는 Bean들을 가져와서 등록해줌

### @ComponentScan

- 빈을 등록하기 위한 어노테이션(@Component)들을 탐색하는 위치를 지정
- 현재 패키지 이하에서 아래와 같은 어노테이션이 붙어 있는 클래스들을 찾아서 빈으로 등록하는 역할

<br><br><br>

참고 자료: <br>
https://mangkyu.tistory.com/211

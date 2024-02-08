## ApplicationContext
기본적인 bean 관리 외에, annotation 기반 설정, 메시지 및 이벤트 처리,국제화,트랜잭션 처리 등 다양한 부가 기능 제공
-> 빈의 생성과 관계설정 외에 추가적인 기능이 필요한데, 이러한 이유로 Spring에서는 빈 팩토리를 상속받아 확장한 애플리케이션 컨텍스트(Application Context)를 주로 사용

<img width="600" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/0bd6b3d5-f5b1-4ed9-8f74-23eac4b82176">

Bean 요청시 처리 과정

1 . ApplicationContext는 @Configuration이 붙은 클래스들을 설정 정보로 등록해두고, @Bean이 붙은 메소드의 이름으로 빈 목록을 생성합니다.(서비스 실행)
2 . 클라이언트가 해당 Bean을 요청합니다.
3 . ApplicationContext는 자신의 빈 목록에서 요청한 이름이 있는지 찾습니다.
4 . ApplicationContext는 설정 클래스로부터 빈 생성을 요청하고, 생성된 빈을 반환해줍니다.

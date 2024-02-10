# ApplicationContext

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
## Spring Boot Framework와 Spring Framework의 차이점

### Dependency
Spring Framework : dependency를 설정해줄 때 설정 파일이 매우 길고, 모든 dependency에 대해 버전 관리도 하나하나 해줘야함
Spring Boot Framework : dependency를 Spring Framework보다 쉽게 설정해 줄 수 있습니다. 버전 관리도 자동으로 해줍니다.
 ex) 빌드 툴을 Gradle을 사용하는 경우 위와 같이 build.gradle파일에 dependency를 추가해주면 Spring Boot로 웹 개발을 할 때 필요한 모든 dependency를 자동으로 추가하고 관리

### Configuration
Spring Framework : configuration설정을 할 때도 매우 길고, 모든 어노테이션 및 빈 등록 등을 설정해 줘야 합니다.
Spring Boot Framework : application.properties파일이나 application.yml파일에 설정하면 됩니다.

### AutoConfiguration
Spring Frame와 달리 Spring Boot에는 AutoConfiguration이라는 것이 있습니다.
Spring Boot로 실행할 수 있는 애플리케이션을 만들기 시작하면 클래스에 @SpringBootApplication이라는 어노테이션을 확인할 수 있습니다.

### 편리한 배포
Spring Framework로 개발한 애플리케이션의 경우, war파일을 Web Application Server에 담아 배포
Spring Boot Framework의 경우, Tomcat 이나 Jetty 같은 내장 WAS를 가지고 있기 때문에 jar 파일로 간편하게 배포할 수 있습니다.

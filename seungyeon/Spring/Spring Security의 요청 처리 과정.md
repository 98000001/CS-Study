# Spring Security의 요청 처리 과정

### 인증(Authentication) 과 인가(Authorization)

- 인증 : 사용자 본인이 맞는지 확인
- 인가 : 사용자가 자원을 사용할 권한이 있는가

### Spring Security

- Spring 기반 애플리케이션의 인증/인가를 담당하는 스프링 하위 프레임워크
- 보안과 관련한 많은 옵션을 제공하기에 보안 관련 로직을 작성하지 않아도 된다는 장점.
- 인증, 권한에 대한 부분을 Filter의 흐름에 따라 처리
    - 스프링 MVC 와 분리되어 관리 및 동작
    - Filter는 DispatcherServlet 으로 가기 전에 적용되어 가장 먼저 요청을 받음
    - Interceptor는 Dispatcher와 controller 사이에 위치해 적용 시기의 차이가 있음
        - Client → `Filter` → `DispatcherServlet` → `Interceptor` → Controller
            - `DispatcherServlet` 은 스프링 MVC에서 가장 먼저 요청받는 것. 요청 받기 전에 다양한 `Filter`가 있을 수 있음
            - `Filter` : 클라이언트와 자원 사이에서 요청/응답 정보를 이용해 다양한 처리를 함
- Spring Security 에서는 Principal 을 아이디로, Credential 을 비밀번호로 사용하는 Credential 기반 인증 방식을 사용한다.
    - Principal ( 접근 주체 ) : 보호 받는 자원에 접근하는 유저
    - Credential ( 비밀번호 ) : 자원에 접근하는 대상의 비밀번호

### [Spring Security의 요청 처리 과정](https://hello-judy-world.tistory.com/216)

![Untitled](https://prod-files-secure.s3.us-west-2.amazonaws.com/b790a1db-0cff-45f3-bfb4-ff5f3db49559/740fe192-04d5-4dd9-9c06-74ad26f2766f/Untitled.png)

- Spring Security 구조
    
    1. 사용자의 요청이 서버로 들어옵니다.
    
    2. Authotication Filter가 요청을 가로채고 Authotication Manger로 요청을 위임합니다.
    
    3. Authotication Manager는 등록된 Authotication Provider를 조회하며 인증을 요구합니다.
    
    4. Authotication Provider가 실제 [데이터](https://www.elancer.co.kr/blog/view?seq=207)를 조회하여 UserDetails 결과를 돌려줍니다.
    
    5. 결과는 SecurityContextHolder에 저장이 되어 저장된 유저정보를 Spring Controller에서 사용할 수 있게 됩니다.
    
1. 사용자가 로그인 정보와 함께 인증 요청
2. Filter가 요청을 가로채고 가로챈 정보를 통해 인증용 객체 생성
3. 등록된 Provider 조회해 인증 요구
4. Provider는 UserDetailsService를 통해 사용자 정보와 DB 값이 일치하면 UserDetails 생성해 반환
    1. UserDetailsService 에서 DB의 사용자 정보 조회
    2. UserDetails 객체는 Authentication 객체를 구현한 UsernamePasswordAuthenticationToken 을 생성하기 위해 사용. 
5. 반환한 UserDetails Filter로 전달
6. Filter는 UserDetails 을 SecurityContextHolder에 저장
7. SecurityContext에 Authentication 객체 저장.
    - 사용자 정보를 저장한다는 것은 Spring Security 전통적인 세션-쿠키 기반의 인증 방식을 사용한다는 것
8. Spring Security 3.2 부터 @AuthenticationPrincipal 을 이용해 로그인한 사용자 객체 확인 가능.
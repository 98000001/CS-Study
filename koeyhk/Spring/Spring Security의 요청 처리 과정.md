# Spring Security의 요청 처리 과정

<img src="https://github.com/98000001/CS-Study/assets/80199502/e6ccf154-d183-472b-9e56-e6869e00cc06"  width="700">

1. 사용자가 로그인 정보와 함께 인증 요청을 한다. (Http Request)
2. AuthenticationFilter가 요청을 가로채고, 가로챈 정보를 통해 UsernamePasswordAuthenticationToken의 인증용 객체를 생성한다.
3. AuthenticationManager의 구현체인 ProviderManager에게 생성한 UsernamePasswordToken 객체를 전달한다.
4. AuthenticationManager는 등록된 AuthenticationProvider(들)을 조회하여 인증을 요구한다.
5. 실제 DB에서 사용자 인증정보를 가져오는 UserDetailsService에 사용자 정보를 넘겨준다.
6. 넘겨받은 사용자 정보를 통해 DB에서 찾은 사용자 정보인 UserDetails 객체를 만든다.
7. AuthenticationProvider(들)은 UserDetails를 넘겨받고 사용자 정보를 비교한다.
8. 인증이 완료되면 권한 등의 사용자 정보를 담은 Authentication 객체를 반환한다.
9. 다시 최초의 AuthenticationFilter에 Authentication 객체가 반환된다.
10. Authenticaton 객체를 SecurityContext에 저장한다.

<br>

### (UsernamePassword)AuthenticationFilter

- 아이디와 비밀번호를 사용하는 form 기반 인증
- 설정된 로그인 URL로 오는 요청을 감시하며, 유저 인증 처리인 AuthenticationManager를 통한 인증 실행
- 인증이 성공한다면 인증용 객체를 SecurityContext에 저장 후 AuthenticationSuccessHandler 실행
- 실패한다면 AuthenticationFailureHandler 실행

### AuthenticationProvider

- 화면에서 입력한 로그인 정보와 DB정보를 비교
- Spring Security의 AuthenticationProvider을 구현한 클래스로 security-context에 provider로 등록 후 인증절차를 구현
- login view에서 login-processing-url로의 form action 진행 시 해당 클래스의 supports() > authenticate() 순으로 인증 절차 진행

### UserDetailsService

- UserDetailsService 인터페이스는 DB에서 유저 정보를 가져오는 역할

### UserDetails

- 사용자의 정보를 담는 인터페이스, 직접 상속받아 사용

<br><br><br><br><br>
참고 자료: <br>
https://dev-coco.tistory.com/174 <br>
https://velog.io/@kyungwoon/Spring-Security-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC

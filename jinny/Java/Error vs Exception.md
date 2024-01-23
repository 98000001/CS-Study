오류(Error): 시스템이 종료되어야 할 수준의 상황 , 수습 불가 , 예측하여 방지 불가 (ex: StackOverflow, OutofMeomoryError)
예외(Exception): 개발자가 구현한 로직에서 발생한 실수나 사용자의 영향에 의해 발생 -> 예외처리를 통해 프로그램을 종료되지 않고 정상적으로 작동되게 만들어줄 수 있다.

둘 다 Throwable클래스를 상속 받음
Trowable 클래스에는 getMessage() pringStackTrace() 함수 구현

![image](https://github.com/98000001/CS-Study/assets/96863137/664f4499-2e04-4856-bab4-d6483662b54f)

컴파일 오류 : .class 파일을 컴파일 하는 과정에서 JVM이 던지는 오류 - 문법적 오류
ClassNotFoundException, IllegalAcessException, NoSuchMethod

런타임 오류 : 컴파일 시에는 정상적으로 컴파일 됐지만 프로그램을 실행하는 과정에서 발생하는 오류
배열의 범위를 벗어남 (IndexOutOfBoundsException), 값이 null인 참조 변수의 멤버를 호출 (NullPointerException)

![image](https://github.com/98000001/CS-Study/assets/96863137/f0e5e690-4c36-4e3e-af17-4e2db5614866)

## 예외 처리
Checked Exception 컴파일 예외클래스
checked exception은 반드시 try - catch 문으로 감싸야함

Unchecked Exception 런타임 예외클래스

Checked / Unchecked Exception으로 재분류 한 이유는 코드적 관점에서 예외 처리 동작을 필수 지정 유무에 따라 나뉘기 때문이다.

![image](https://github.com/98000001/CS-Study/assets/96863137/9a282423-25c0-4c98-8e89-03f75d77618a)

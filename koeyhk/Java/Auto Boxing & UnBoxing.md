## Auto Boxing & UnBoxing

Java 1.5 Version에 도입된 기능으로, 원시 타입(Primitive Type)에서 래퍼 클래스(Wrapper Class) 타입으로 또는 반대로 자동 변환하는 것

- 래퍼 클래스(wrapper class) - 기본 타입(primitive type)을 객체로 다루기 위해서 사용하는 클래스

<img src="https://github.com/98000001/CS-Study/assets/80199502/2a244d37-ec1e-4a83-b1df-b16f971c4070"  width="500">

<br>

### Auto Boxing

- 원시 타입의 값을 해당하는 wrapper 클래스의 객체로 변환시켜 주는 것
- ex) int → Integer, double → Double
- 변환 과정에서 메모리의 동적 할당과 각 원시 타입에 대한 객체 초기화가 포함되며, 객체를 명시적으로 생성할 필요가 없음
- 자바 컴파일러는 원시 타입이 아래 두 가지 경우에 해당될 때 autoBoxing을 적용
    - 원시타입이 Wrapper 클래스의 타입의 파라미터를 받는 메서드를 통과할 때
    - 원시 타입이 Wrapper 클래스의 변수로 할당될 때

### UnBoxing

- Wrapper 클래스 타입을 원시 타입으로 변환시켜 주는 것
- 자바 컴파일러는 원시타입이 아래 두 가지 경우에 해당될 때 unBoxing을 적용
    - Wrapper 클래스 타입이 원시 타입의 파라미터를 받는 메서드를 통과할 때
    - Wrapper 클래스 타입이 원시 타입의 변수로 할당될 때

<br>

### Auto Boxing & UnBoxing 특징

- 자동으로 타입 변환이 발생하므로 명시적으로 타입을 변환하지 않아도 됨
- 오토박싱은 코드에서 보이지 않지만 래퍼 클래스 객체에 값을 할당하기 위해 객체를 생성 (성능 저하)

<br><br><br><br><br>

참고자료: <br>
https://velog.io/@wkdwoo/AutoBoxing%EC%98%A4%ED%86%A0-%EB%B0%95%EC%8B%B1-UnBoxing%EC%96%B8%EB%B0%95%EC%8B%B1 <br>
https://developer-talk.tistory.com/504

# Default Method

- 메소드 선언 시에 default를 명시하게 되면 인터페이스 내부에서도 로직이 포함된 메소드를 선언할 수 있음
- 접근제어자에서 사용하는 default와 같은 키워드이지만, 인터페이스의 default method는 `default`라는 키워드를 명시해야 함
- 추상 메서드와 다른 점
    - 메서드 앞에 `default` 예약어를 붙임
    - 구현부 `{}` 가 있어야 함

```java
interface MyInterface { 
    default void printHello() {
    	System.out.println("Hello World"); 
        } 
} 

class MyClass implements MyInterface {} 

public class DefaultMethod { 
    public static void main(String[] args) { 
    	MyClass myClass = new MyClass(); 
        myClass.printHello(); //실행결과 Hello World 출력 
    } 
}
```

<br>

### 사용 이유

인터페이스의 기본 구현을 제공할 수 있도록 디폴트 메서드(default method) 기능을 사용

- 인터페이스에 추상메서드를 추가하게 되면 모든 구현체에 구현을 해야 하지만, default 메소드를 추가하게 된다면 하위 호환성은 유지되고 인터페이스의 보완을 진행 가능
- OCP(개방 폐쇄 원칙)에서 확장에 개방(Open)되어 있고, 변경에 닫혀(Close)있는 코드를 설계 가능

<br><br><br><br><br>

참고 자료: <br>
https://siyoon210.tistory.com/95 <br>
[https://velog.io/@heoseungyeon/디폴트-메서드Default-Method](https://velog.io/@heoseungyeon/%EB%94%94%ED%8F%B4%ED%8A%B8-%EB%A9%94%EC%84%9C%EB%93%9CDefault-Method)

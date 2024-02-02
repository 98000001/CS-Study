## 1. Default Method

인터페이스는 기능에 대한 선언만 하고 실제 구현 코드는 포함할 수 없다.  
하지만 Default Method를 사용하면 인터페이스 내부에도 구현이 포함된 메서드를 포함할 수 있다.  
인터페이스의 Default Method는 default라는 키워드를 명시해야 한다.

```java
interface TestInterface {
    default void print() {
        System.out.println("Hello world");
    }
}
```

인터페이스는 기능에 대한 구현보다 기능에 대한 선언에 초점을 맞춘다.  
인터페이스 보완 과정에서 메서드를 추가한다면 구현한 클래스와의 호환성이 떨어진다.  
이때 Default Method를 추가하면 하위 호환성은 유지되고 인터페이스의 수정이 가능하다.
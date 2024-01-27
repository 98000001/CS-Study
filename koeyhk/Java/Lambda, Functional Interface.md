## Lambda Expression

- 함수를 하나의 식(expression)으로 표현한 것
- 메소드의 이름이 필요 없기 때문에, 람다식은 익명 함수(Anonymous Function)의 한 종류
- 익명함수(Anonymous Function)란 함수의 이름이 없는 함수로, 익명함수들은 모두 일급 객체
- 람다 방식으로는 메소드 명이 불필요하며, 괄호 () 와 화살표 -> 를 이용해 함수를 선언
- 람다식으로 생성된 순수 함수는 함수형 인터페이스로만 선언 가능
- 장점: 불필요한 코드를 줄이고, 가독성과 생산성이 높아짐
- 단점: 디버깅이 어렵고 재사용이 불가능함

```java
// 기존 표현 방식
int sum(int num1, int num2) {
    return num1 + num2;
}

// 람다식
(int num1, int num2) -> {
    num1 + num2
}
```

<br>

## 함수형 인터페이스(Functional Interface)

- 함수를 1급 객체처럼 다룰 수 있게 해주는 어노테이션
- **함수형 인터페이스는 단 하나의 추상 메서드만을 선언 가능**
- Java의 람다식은 함수형 인터페이스로만 접근 가능
- 함수를 변수처럼 선언하는 것이 가능하고, 코드를 간결하게 작성 가능

```java
@FunctionalInterface
interface FunctionalEx {
    public abstract int sum(int num1, int num2);
}

public class LambdaTest {
    public static void main(String[] args) {
        FunctionalEx functionalEx = (num1, num2) -> num1 + num2;
        System.out.println(functionalEx.sum(10, 15));
    }
}
```


<br><br><br><br><br>

참고 자료: <br>
https://mangkyu.tistory.com/111 <br>
https://ittrue.tistory.com/161

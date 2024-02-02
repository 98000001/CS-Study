# Generic

**클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법**

**장점**

- 잘못된 타입이 들어올 수 있는 것을 컴파일 단계에서 방지
- 타입에 대해 유연성과 안정성을 확보한다.
- 비슷한 기능을 지원하는 경우 코드의 재사용성이 높아짐

```java
List<Integer> list = new ArrayList<>();
Map<String, Integer> map = new HashMap<>();
```

<br>

### Generic 사용 이유

- 타입을 유연하게 처리하며, 잘못된 타입 사용으로 발생할 수 있는 런타임 타입 에러를 컴파일 과정에 검출하기 위함

<br>

### Generic 사용방법

- 클래스, 인터페이스 또는 메소드에 선언 가능
- 동시에 여러 타입을 선언 가능
- 와일드 카드를 이용하여 타입에 대하여 유연한 처리 가능
- 제네릭 선언 및 정의시에 타입의 상속 관계를 지정 가능

```java
public class MyClass<T>
public interface MyInterface<T>
```

- 타입 파라미터의 정해진 규칙은 없지만 일반적으로 대문자 알파벳 한글자로 표현함

### 자주 사용하는 타입인자

| 타입 | 설명 |
| --- | --- |
| T | Type |
| E | Element |
| K | Key |
| V | Value |
| N | Number |

<br><br><br><br><br>

참고 자료: <br>
https://hahahoho5915.tistory.com/69

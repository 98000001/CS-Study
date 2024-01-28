## 1. 람다 표현식

람다 표현식은 메서드로 전달할 수 있는 익명 함수를 단순화한 것이다.  
람다 표현식에는 이름은 없지만, 파라미터 리스트, 바디, 변환 형식, 발생할 수 있는 예외 리스트를 가질 수 있다.

### 1-1. 특징

- 익명 : 보통의 메서드와 달리 이름이 없으므로 익명이라 표현한다.
- 함수 : 람다는 메서드처럼 특정 클래스에 종속되지 않으므로 함수라고 부른다.
- 전달 : 람다 표현식을 메서드 인수로 전달하거나 변수로 저장할 수 있다.
- 간결성 : 익명 클래스처럼 많은 코드를 구현할 필요가 없다.

람다 표현식을 이용하면 동적 파라미터 형식의 코드를 더 쉽게 구현할 수 있다.  
람다 표현식은 파라미터 리스트, 화살표, 바디 세 부분으로 이루어진다.

```java
// 기존
Comparator<Apple> byWeight = new Comparator<Apple>() {
    public int compare(Apple a1, Apple a2) {
        return a1.getWeight().compareTo(a2.getWeight());
    }
};

// 람다
Comparator<Apple> byWeight = (Apple a1, Apple a2) ->
        a1.getWeight().compareTo(a2.getWeight());
```

### 1-2. 함수형 인터페이스

```java
public interface Predicate<T> {
    boolean test(T t);
}

public interface Comparator<T> {
    int compare(T o1, T o2);
}

public interface Runnable {
    void run();
}
```

위와 같이 함수형 인터페이스는 정확히 하나의 추상의 메서드를 지정하는 인터페이스다.  
Default 메서드를 포함하고 있더라도 추상 메서드가 하나면 함수형 인터페이스다.  
람다 표현식으로 함수형 인터페이스의 추상 메서드 구현을 직접 전달할 수 있다.  
즉, 전체 표현식을 함수형 인터페이스의 인스턴스로 취급할 수 있다.

```java
Runnable r1 = () -> System.out.println("a");
Runnable r2 = new Runnable() {
    public void run() {
        System.out.println("b");
    }
};

public static void process(Runnable r) {
    r.run();
}

process(r1); // 람다

process(r2); // 익명 클래스

process(() ->System.out.

println("c")); // 직접 전달한 람다 표현식
```

### 1-3. 함수형 디스크립터

함수형 인터페이스의 추상 메서드 시그니처는 람다 표현식의 시그니처를 가리킨다.  
람다 표현식의 시그니처를 서술하는 메서드를 함수 디스크립터라고 부른다.  
위 코드 Runnable 인터페이스의 유일한 추상 메서드 run은 인수와 반환 값이 없다.  
그래서 인수와 반환 값이 없는 시그니처라고 할 수 있다.

```java
public void process(Runnable r) {
    r.run();
}
// 유효함
process(() -> System.out.println("Lambda"));

// 유효하지 않음
Predicate<Apple> p = (Apple a) -> a.getWeight();
```

첫 번째 코드는 람다 표현식의 시그니처가 동일하기 때문에 유효하다.  
두 번째 코드는 람다 표현식의 시그니처가 일치하지 않아서 유효하지 않다.

> **@FunctionalInterface**  
> 함수형 인터페이스임을 가리키는 어노테이션이다.  
> 선언했지만 실제로 함수형 인터페이스가 아니라면 컴파일 에러가 발생한다.
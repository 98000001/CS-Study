# Java 8 특징

## 람다 표현식 (Lambda Expression)

- 메소드를 하나의 식으로 표현한 것
- 함수의 이름이 없기 때문에 익명 함수라고 부르며, 메소드의 매개 변수로 전달되거나 메소드의 결과로 반환될 수 있는 특징이 있어서 함수를 변수로 다룰 수 있다는 장점 존재

```java
// 외부 반복
for (String value: myCollection) { 
    System.out.println(value); 
}

// 내부 반복
myCollection.forEach(value -> System.out.println(value));
```

<br>

## 함수형 인터페이스

- 하나의 기능을 제공하는 단 하나의 추상 메소드를 정의하는 인터페이스
- 함수를 일급객체처럼 다룰 수 있게 함수형 인터페이스를 제공
- 함수를 하나의 값으로 취급해서, 함수들을 조립하고 배치하면서 개발 가능

```java
@FunctionalInterface
public interface Car {
	String drive(int driveLevel);
}

// 인터페이스 사용
// 1. 전통적인 방법
Car car = new Car() {
	@Override
    public String drive(int driveLevel) {
    	return driveLevel == 0 ? "" : "자동차가 " + driveLevel + " 의 속도로 이동";
    }
};
System.out.println(car.drive(10));

// 2. 람다 표현식
Car car = (i) -> i == 0 ? "" : "자동차가 " + driveLevel + " 의 속도로 이동";
System.out.println(car.drive(10));
```

<br>

## Default method, **static method**

- 인터에페이스는 구현부가 없는 추상메소드만 가질 수 있었는데 default, static 지시어로 생성된 메서드는 구현부를 가질 수 있음
- default method: 재정의 o, 참조 변수로 호출
- static method: 재정의 x, 객체 생성하지 않고 사용
- 하위 호환성을 유지하고 인터페이스 보완 가능 (인터페이스가 갖는 추상 메서드 구현의 강제성이 사라짐)

```java
public interface Car {
		void drive();

    default void fly() {
    	System.out.println("Fly");
    }
		static int sumStatic(int x, int y) {
        return x + y;
    }
}
```

<br>

## Stream

- 스트림은 Collection을 멋지고 편리하게 처리하는 방법을 제공하는 API
- 처리 방법을 고민하지 않고 원하는 값을 정하면 적절한 방법으로 처리하여 값을 돌려줌

```java
// 기존 코드
books.sort(Comparator.comparing(Book::getName));

List<String> books = new ArrayList<>();
for (Book book : books) {
	if (book.getAuthor().equals("Chancehee")) {
    	books.add(book.getIsbn());
    }
}

// 스트림 사용
List<String> books =
	books.stream()
    	.filter(book -> book.getAuthor().equals("Chancehee"))
        .sorted(Comparator.comparing(Book::getName))
        .map(Book::getIsbn)
        .collect(Collecors.toList());
```

<br>

## Optional

- Java가 가지고 있는 null의 문제점을 보완하고자 등장 (Wrapper class)
- 비즈니스 코드와 null 방어 코드가 뒤섞이지 않는다는 장점

```java
public class BookService {
	public Optional<String> getAuthorName(Book book) {
    	return Optional.ofNullable(book)
        	.map(bookObject -> bookObject.getAuthor())
            .map(authorObject -> authorObject.getName());
    }
}
```

<br><br><br><br><br>

참고 자료: <br>
https://velog.io/@chancehee/Java-Java-8-11-%EB%B2%84%EC%A0%84-%ED%8A%B9%EC%A7%95 <br>
https://velog.io/@skyepodium/%EC%9E%90%EB%B0%94-Java-8-%EB%B2%84%EC%A0%84-%ED%8A%B9%EC%A7%95

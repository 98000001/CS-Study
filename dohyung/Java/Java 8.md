## 1. Java 8 특징

### 1-1. 람다 표현식

람다 표현식은 메서드로 전달할 수 있는 익명 함수를 단순화한 것이다.  
람다 표현식에는 이름은 없지만, 파라미터 리스트, 바디, 반환 형식 등을 가질 수 있다.

```java
Predicate<Dog> p = (Dog d) -> d.getWeight();
```

### 1-2. 메서드 참조

메서드 참조는 람다 표현식을 축약한 형태다.  
적절하게 사용하면 가독성이 좋아진다.

```java
Predicate<Dog> p = Dog::getWeight;
```

### 1-3. Interface의 Default Method

Java 8 이전에는 인터페이스에 선언만 할 수 있었다.  
Java 8 부터는 인터페이스에 default 메서드를 선언하고 구현 내용을 포함할 수 있다.

```java
public interface Car {
    default void run() {
        System.out.println("출발");
    }
}
```

### 1-4. Optional

Java 8 부터 Optional을 활용해서 비어있는 값을 정의할 수 있다.  
`NullPointerException`에 잘 대응할 수 있다.

```java
// 생성
Optional<String> name = Optional.of("kim");
Optional<String> nullableName = Optional.ofNullable("kim");

// 추출
String nameStr = name.orElse("kim");

// 확인
if(name.isEmpty()){
    System.out.println("isEmpty");
}
```

### 1-5. Stream API
Java 8 부터 순차, 병렬 작업을 지원하는 Stream API가 추가되었다.  
Stream은 선언형으로 컬렉션 데이터를 처리할 수 있다.  
선언형이란 데이터를 처리하는 구현 코드 대신, 질의로 표현하는 것을 말한다.

```java
List<String> highRatingMoviesName =
        movies.stream()
                .filter(m -> m.getRating() > 7) // 평점 7 이상 영화 선택
                .sorted(comparing(Movie::getRating)) // 평점 순으로 정렬
                .map(Movie::getName) // 영화명 추출
                .collect(Collectors.toList()); // 리스트에 저장
```

### 1-6. 새로운 날짜, 시간 API

기존 Date와 Calendar 클래스의 기능 부족과 명명 규칙이 비표준적이었다.  
그리고 일관되지 못한 속성 값의 문제를 해결하기 위해 새로운 날짜 API가 추가되었다.

```java
//javax.time.Clock
Clock.systemUTC();					//current time of your system in UTC. 
Clock.millis();						//time in milliseconds from 1/1/1970.

//javax.tme.ZoneId
ZoneId zone = ZoneId.of(“Europe/London”);		//zoneId from a timezone. 
Clock clock = Clock.system(zone);			//set the zone of a Clock.

//javax.time.LocalDate
LocalDate date = LocalDate.now();			//current date 
String day = date.getDayOfMonth();			//day of the month 
String month = date.getMonthValue();			//month 
String year = date.getYear();				//year
```
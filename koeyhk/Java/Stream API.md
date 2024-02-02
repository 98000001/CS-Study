# Stream API

- 스트림(Stream) API은 람다식(Lambda Expression)를 이용한 기술 중에 하나로 데이터 소스(컬렉션, 배열, 난수, 파일 등…)를 조작 및 가공, 변환하여 원하는 값으로 반환해주는 인터페이스를 의미
- 해당 기능을 사용하기 위해서는 Java 1.8 이상의 버전을 사용해야 함

### 특징

- 원본 데이터를 변경하지 않고, 외부 반복을 통해 작업하는 컬렉션과는 달리 내부 반복을 통해 작업을 수행
- 재사용이 가능한 컬렉션과는 달리 단 한 번만 사용 가능
- 연산은 필터(filter)-맵(map) 기반의 API를 사용하여 지연(lazy) 연산을 통해 성능을 최적화함
- parallelStream() 메서드를 통한 손쉬운 병렬 처리를 지원
- 스트림의 생성 -> 스트림의 중개 연산 -> 스트림의 최종 연산 세 가지 단계에 걸쳐서 동작하며, 중개 연산의 경우 Stream형태로 결과를 반환하기 때문에 연속적으로 연결해서 사용 가능

<br>

### **스트림의 생성**

스트림 API는 다양한 데이터 소스에 적용 가능

- 컬렉션

```java
// 컬렉션에서 스트림 생성
Stream<Integer> stream = list.stream();

// forEach() 메소드를 이용한 스트림 요소의 순차 접근
stream.forEach(System.out::println);
```

- 배열

```java
// 배열에서 스트림 생성
Stream<String> stream1 = Arrays.stream(arr);
stream1.forEach(e -> System.out.print(e + " "));
System.out.println();
```

- 람다 표현식

```java
// generate()
Stream<Double> randomStream = Stream.generate(Math::random);
Stream<Integer> oneStream = Stream.generate(()->1);
```

- 가변 매개변수
- 지정된 범위의 연속된 정수
- 특정 타입 난수들
- 파일
- 빈 스트림

<br>

### **스트림의 중간(중개) 연산(intermediate operation)**

생성된 스트림을 이용해 필요한 데이터를 만드는 단계

- 스트림 필터링: filter(), distinct()
- 스트림 변환: map(), flatMap()
- 스트림 제한: limit(), skip()
- 스트림 정렬: sorted()
- 스트림 연산결과 확인: peek()

<br>

### **스트림 최종 연산(terminal operation)**

스트림 객체는 마지막 최종 연산으로 요소를 소모하고, 결과를 표시

- 요소의 출력 : forEach()
- 요소의 소모 : reduce()
- 요소의 검색 : findFirst(), findAny()
- 요소의 검사 : anyMatch(), allMatch(), noneMatch()
- 요소의 통계 : count(), min(), max()
- 요소의 연산 : sum(), average()
- 요소의 수집 : collect()

<br><br><br><br><br>

참고 자료: <br>
https://jong99.tistory.com/177

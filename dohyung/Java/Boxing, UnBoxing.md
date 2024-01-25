## 1. Wrapper Class

### 1-1. Wrapper Class란 ?

Primitive Type을 객체로 다루기 위해 사용하는 클래스들을 Wrapper Class라고 한다.  
기본 타입의 값을 내부에 두고 포장하기 때문에 포장 객체라고도 불린다.  
외부에서 변경이 불가능하고, 만약 값을 변경하고 싶다면 새로운 포장 객체를 만들어야 한다.

Wrapper Class를 사용하는 이유는 아래와 같다.

- Generic은 참조 타입만을 허용하기 때문에 Wrapper Class로 쓸 수 있다.
- Collection Framework은 기본 타입이 아닌 객체만 저장할 수 있다.
- Wrapper Class를 사용하면 Null 값을 허용할 수 있다.

### 1-2. Wrapper Class의 특징

### 연산

Auto Boxing, Auto UnBoxing 기능을 이용해서 Wrapper Class 객체끼리 직접 연산이 가능하다.

### 동등 비교

Wrapper Class 객체를 `==`으로 비교하면 객체의 주소 값을 비교한다.  
그래서 포장 내부의 값을 UnBoxing해서 비교하거나 `equals()` 메서드를 통해 직접 비교가 가능하다.  
Wrapper Class 객체와 기본 자료형과의 비교는 Auto 기능 덕분에 `==`와 `equals()` 연산 모두 가능하다.

### 변환

객체를 포장하는 기능 외에도, Wrapper Class는 자체 지원하는 parse타입() 메서드를 이용해서 데이터 타입 변환이 가능하다.

## 2. Boxing, UnBoxing

### 2-1. Boxing, UnBoxing

Boxing : 기본 타입의 데이터 -> 래퍼 클래스의 인스턴스로 변환  
UnBoxing : 래퍼 클래스의 인스턴스에 저장된 값 -> 기본 타입의 데이터로 변환

### 2-2. Auto Boxing, Auto UnBoxing

JDK 일정 버전 이후에는 Boxing과 UnBoxing이 필요한 상황에 Java 컴파일러가 자동으로 처리해준다.

```java
Integer num1 = new Integer(25); // Boxing
int num2 = num.intValue(); // UnBoxing

Integer num1 = 25; // new Integer() 생략, Auto Boxing
int num2 = num1; // intValue(), Auto UnBoxing
```
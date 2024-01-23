# Error vs Exception

<img src="https://github.com/98000001/CS-Study/assets/80199502/049e9d60-b580-4924-9b9b-036a9b8ca0d8"  width="700">

### Throwable

- 오류와 예외 모두 자바의 최상위 클래스인 Object를 상속받고, 그 사이에는 Throwable이라는 클래스와 상속관계가 있음

<br>

## 오류(Error)

<img src="https://github.com/98000001/CS-Study/assets/80199502/55d83a0d-82da-44d6-a0af-917f5374d1e2"  width="650">

- 오류(Error)는 시스템이 종료되어야 할 수준의 상황과 같이 수습할 수 없는 심각한 문제를 의미
- 컴파일 시 문법적인 오류와 런타임 시 널포인트 참조와 같은 오류로 프로세스에 심각한 문제를 야기 시켜 프로세스를 종료 시킬 수 있음

<br>

### **StackOverflowError**

응용 프로그램이 너무 많이 반복되어 StackOverflow가 발생할 때 던져지는 오류

### **OutOfMemoryError**

JVM이 할당된 메모리의 부족으로 더 이상 객체를 할당할 수 없을 때 던져지는 오류

- Garbage Collector에 의해 추가적인 메모리가 확보되지 못하는 상황일 때
- heap 사이즈 부족
- 너무 많은 class를 로드할 때
- 가용가능한 swap이 없을 때
- 큰 메모리의 native메서드가 호출될 때
- 해결책: dump 파일 분석, jvm 옵션 수정 등

<br>

## 예외(Exception)

<img src="https://github.com/98000001/CS-Study/assets/80199502/3c96bae5-71a7-40f8-b795-ee825a8947ae"  width="680">

- 예외(Exception)는 개발자가 구현한 로직에서 발생한 실수나 사용자의 영향에 의해 발생
- 오류와 달리 개발자가 예측하여 방지할 수 있어 상황에 맞는 예외처리(Exception Handle)를 해야 함
- 예외처리(Exception Handling)를 통해 프로그램이 종료되지 않고 정상적으로 작동되게 만들어줄 수 있음

<br>

### **Checked Exception**

- 예외처리가 필수이며, 처리하지 않으면 컴파일되지 않음
- try-catch로 감싸거나 throw로 던져서 예외처리
- 컴파일 단계에서 명확하게 Exception체크가 가능 (Runtime Exception)
- 예외 발생시 트랜잭션을 roll-back 하지 않고 예외를 던짐
- JVM 외부와 통신(네트워크, 파일시스템 등)할 때 주로 쓰임
- IOException, SQLException 등

### **UncheckedException**

- RuntimeException 하위의 모든 예외
- NullPointerException, IndexOutOfBoundException 등
- 실행과정 중 어떠한 특정 논리에 의해 발견되는 Exception
- 예외 발생시 트랜잭션을 roll-back함
- 명시적인 예외처리를 하지 않아도 됨
- NullPointerException, IndexOutOfBoundException 등

<br>

### Exception Handling

Java에서 모든 예외가 발생하면 (XXX)Exception 객체를 생성

**처리 방법 2가지**

1. 직접 `try-catch`를 이용해서 예외에 대한 최종적인 책임을 지고 처리하는 방식
2. `throws Exception`을 이용해서 발생한 예외의 책임을 호출하는 쪽이 책임지도록 하는 방식 (주로 호출하는 쪽에 예외를 보고할 때 사용함)다른 메서드의 일부분으로 동작하는 경우엔 던지는 것을 추천.



<br>
<br>
<br>
<br>
<br>
<br>

참고 자료: <br>
https://velog.io/@jipark09/Java-Error%EC%99%80-Exception-%EC%B0%A8%EC%9D%B4

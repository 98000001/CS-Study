# 비동기 처리

**Thread** - 프로세스의 내부에서 실행되는 흐름의 단위

<br>

## 동기식 처리 (Synchronous)

<img src="https://github.com/98000001/CS-Study/assets/80199502/e55d04f8-1bd4-46bf-bf7f-05464a0c9fcc"  width="600">

- 직렬적으로 task를 수행
- task는 순차적으로 실행되며, 어떤 작업이 수행 중이면 다음 작업은 대기하게 됨
- 작업을 설계하거나 작업의 흐름에 대해서 파악하기 쉬움
- 다른 스레드에서 접근할 수 없기 때문에 안정적인 작업이 가능 (Thread Safe 스레드 안전)

```java
package Synchro_Asynchro;

public class Synchro {
	public static void main(String[] args) {
		
		method1();
		method2();
		method3();
		
	}
	
	public static void method1() {
		System.out.println("method1");
	}
	public static void method2() {
		System.out.println("method2");
	}
	public static void method3() {
		System.out.println("method3");
	}
	
}

// *Print*
// method1
// method2
// method3
```

<br>

## 비동기식 처리 (Asynchronous)

<img src="https://github.com/98000001/CS-Study/assets/80199502/dd256c09-2e4f-4d74-984e-257402ac5def"  width="600">

- Non-Blocking processing model로 병렬적으로 task를 수행
- task가 종료되지 않은 상태라 하더라도 대기하지 않고 다음 task를 실행
- 장점 : 요청에 따른 결과가 반환되는 시간 동안 다른 작업을 수행할 수 있음
- 단점 : 동기식보다 설계가 복잡하고 논증적임
- ex) 서버에서 데이터를 가져와서 화면에 표시하는 task를 수행할 때, 서버에 데이터를 요청한 이후 서버로부터 데이터가 응답될 때까지 대기하지 않고(Non-Blocking) 즉시 다음 task를 수행한다. 이후 서버로부터 데이터가 응답되면 이벤트가 발생하고 이벤트 핸들러가 데이터를 가지고 수행할 task를 계속해 수행한다. 자바에서는 대표적으로 Multi Thread의 동작이 비동기식으로 작동한다.

```java
package Synchro_Asynchro;

public class Asynchro {
	public static void main(String[] args) {
	
	
		Thread t = new Thread(()->{
			method1();
		});
		Thread t2 = new Thread(()->{
			method2();
		});
		Thread t3 = new Thread(()->{
			method3();
		});
		
		
		t.start();
		t2.start();
		t3.start();
		
	}
	
	public static void method1() {
		System.out.println("method1");
	}
	public static void method2() {
		System.out.println("method2");
	}
	public static void method3() {
		System.out.println("method3");
	}
}

// *Print* -> 실행할 때마다 순서가 바뀜
// method1
// method3
// method2
```

<br>

## Java 비동기 처리 방식

### Callback

**CompletionHandler**를 사용할 수도 있고, **함수형 인터페이스**를 이용해서 구현 가능

1. **CompletionHandler**
- 비동기 I/O 작업의 결과를 처리하기 위한 목적으로 만들어졌으며, 콜백 객체를 만드는 데 사용됨
- `completed()` 메소드를 오버라이드해서 콜백을 구현하고, `failed()` 메소드를 오버라이드해 작업이 실패했을 때의 처리를 구현
- `try-catch`나 `if`문을 이용해 작업이 성공했는지 판단한 뒤 작업이 성공했으면 콜백 객체의 `completed()`를 호출하고, 실패했거나 예외가 발생했으면 `failed()`를 호출

2. **함수형 인터페이스**
- 작업1을 마친 뒤 callback으로 받아온 함수형 인터페이스를 실행하는 메소드를 호출
- `execute()`의 인자로 `execute()`의 작업이 모두 끝난 뒤 실행될 콜백을 작성해 넣어야 함

<br>

### Future

- `Future` 객체를 사용한 비동기 처리 방식은 다른 주체에게 작업을 맡긴 상태에서 본 주체 쪽에서 작업이 끝났는지 물어보면서 직접 확인하는 방식
- 확인하는 방법 두 가지
    1. `isDone()`이나 `isCanceled()` 메소드로 블로킹 없이 작업을 완료했는지의 여부만 확인하는 방법
    2. `get()`으로 작업이 완료될 때까지 블로킹된 상태로 대기하는 방법
 

<br><br><br><br><br><br>


참고 자료: <br>
https://webheck.tistory.com/entry/Java%EB%8F%99%EA%B8%B0%EC%99%80-%EB%B9%84%EB%8F%99%EA%B8%B0-%EB%B0%A9%EC%8B%9DAsynchronous-processing-model <br>
https://velog.io/@pllap/Java%EC%97%90%EC%84%9C%EC%9D%98-%EB%B9%84%EB%8F%99%EA%B8%B0-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D

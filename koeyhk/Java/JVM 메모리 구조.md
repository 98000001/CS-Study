## **JVM (Java Virtual Machine)**

- 자바 가상 머신
- 자바와 운영체제 사이에서 중개자 역할을 수행하며, 자바가 운영체제에 구애 받지 않고 프로그램을 실행할 수 있도록 도와줌
- 가비지 컬렉터를 사용한 자동적인 메모리 관리, 스택 기반으로 동작

### JVM 동작 방식

<img src="https://github.com/98000001/CS-Study/assets/80199502/f94c8987-83fc-4772-a47a-622e83af79f7"  width="500">

<br>

1. 자바로 개발된 프로그램을 실행하면 JVM은 OS로부터 메모리를 할당
2. 자바 컴파일러(javac)가 자바 소스코드(.java)를 자바 바이트코드(.class)로 컴파일
3. Class Loader를 통해 JVM Runtime Data Area로 로딩
4. Runtime Data Area에 로딩 된 .class들은 Execution Engine을 통해 해석
5. 해석된 바이트 코드는 Runtime Data Area의 각 영역에 배치되어 수행하며 이 과정에서 Execution Engine에 의해 GC의 작동과 스레드 동기화가 이루어짐

<br>

## **JVM 메모리 구조**

Garbage Collector, Execution Engine, Class Loader, Runtime Data Area로, 4가지로 나눌 수 있음

### (1) 클래스 로더 (Class Loader)

<img src="https://github.com/98000001/CS-Study/assets/80199502/0da9d20b-1204-4252-95a0-e47502100886"  width="500">

<br>

- JVM 내로 클래스 파일을 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈
- 런타임 시에 동적으로 클래스를 로드

### **(2) 실행 엔진 (Execution Engine)**

- 클래스 로더를 통해 JVM 내의 Runtime Data Area에 배치된 바이트 코드들을 명렁어 단위로 읽어서 실행

### **(3) 가비지 컬렉터 (Garbage Collector)**

<img src="https://github.com/98000001/CS-Study/assets/80199502/a37526d0-3efb-465c-b418-585362259509"  width="500">

- GC는 힙 메모리 영역에 생성된 객체들 중에서 참조되지 않은 객체들을 탐색 후 제거하는 역할

### **(4) 런타임 데이터 영역 (Runtime Data Area)**

<img src="https://github.com/98000001/CS-Study/assets/80199502/8943d459-2f3a-4e4e-9d0e-f69e4a4d7c97"  width="800">

- JVM의 메모리 영역으로 자바 애플리케이션을 실행할 때 사용되는 데이터들을 적재하는 영역
- 크게 Method Area, Heap Area, Stack Area, PC Register, Native Method Stack로 나눌 수 있음

**모든 스레드가 공유해서 사용 (GC의 대상)**

- 힙 영역 (Heap Area)
- 메서드 영역(Method Area)

**스레드(Thread) 마다 하나씩 생성**

- 스택 영역(Stack Area)
- PC 레지스터 (PC Register)
- 네이티브 메서드 스택(Native Method Stack)

<br>

**메서드 영역 (Method Area)**

- 클래스, 인터페이스, 메소드, 필드, Static 변수 등이 생성되는 영역

**힙 영역 (Heap Area)**

- new 키워드로 생성된 객체와 배열이 생성되는 영역
- 주기적으로 GC가 제거하는 영역

**스택 영역 (Stack Area)**

- 지역변수, 파라미터, 리턴 값, 연산에 사용되는 임시 값 등이 생성되는 영역
- 메서드 수행이 끝나면 프레임별로 삭제

**PC 레지스터 (PC Register)**

- Thread가 생성될 때마다 생성되는 영역
- 프로그램 카운터, 즉 현재 스레드가 실행되는 부분의 주소와 명령을 저장하고 있는 영역

**네이티브 메서드 스택 (Native Method Stack)**

- 자바 외 언어로 작성된 네이티브 코드를 위한 메모리 영역 (보통 C/C++ 등의 코드를 수행하기 위한 스택)

<br>
<br>
<br>
<br>
<br>

참고 자료: https://coding-factory.tistory.com/828

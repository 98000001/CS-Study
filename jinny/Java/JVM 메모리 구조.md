### 클래스 로더(Class Loader)
자바는 동적으로 클래스를 읽어오므로, 프로그램이 실행 중인 런타임에서야 모든 코드가 자바 가상 머신과 연결됨
동적으로 클래스를 로딩해주는 역할을 하는 것
클래스 로더는 .class 파일을 묶어서 JVM이 운영체제로부터 할당받은 메모리 영역인 Runtime Data Area로 적재

### 실행 엔진(Execution Engine)
Runtime Data Area의 Method Area에 배치되는데
JVM은 Method Area의 바이트 코드를 실행 엔진(Execution Engine)에 제공하여, 
정의된 내용대로 바이트 코드를 실행시킴

### 가비지 컬렉터(Garbage Collector)
가비지 컬렉터(garbage collector)를 이용하여 더는 사용하지 않는 메모리를 자동으로 회수해줌
###### Heap 메모리 영역에 생성(적재)된 객체들 중에 참조되지 않은 객체들을 탐색 후 제거하는 역할

### 런타임 데이터 영역 (Runtime Data Area) -> JVM의 메모리 영역 -> 자바 애플리케이션을 실행할 때 사용되는 데이터들을 적재하는 영역

![image](https://github.com/98000001/CS-Study/assets/96863137/ed97662d-2e99-4e5e-b2ad-5ea0bfcf20b2)


모든 스레드가 공유해서 사용 
힙 영역 (Heap Area)
메서드 영역(Method Area)

스레드(Thread) 마다 하나씩 생성
스택 영역(Stack Area)
PC 레지스터 (PC Register)
네이티브 메서드 스택(Native Method Stack)

### 힙 영역 (Heap Area)
- new 키워드로 생성된 객체와 배열이 생성되는 영역입니다. 
- 주기적으로 GC가 제거하는 영역입니다.

![image](https://github.com/98000001/CS-Study/assets/96863137/6f5d49f8-1837-4d25-a280-407cb32e5ae8)

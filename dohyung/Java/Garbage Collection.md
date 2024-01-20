## 1. GC란 ?

GC(Garbage Collection)는 자바 Application에서 사용하지 않는 메모리를 자동으로 수거하는 기능이다.  
특히 `Heap` 영역에 동적으로 할당된 객체 중 불필요한 객체를 찾는다.  
C/C++ 같은 언어는 메모리를 직접 할당/해제를 하지만, Java에서는 GC를 덕분에 개발자들이 메모리 관리를 비교적 신경쓰지 않아도 된다.

### 1-1 GC의 수거 대상

어떤 객체가 Garbage일까 ?
GC는 객체를 Reachable, Unreachable 상태를 구분한다.
> 유효한 참조가 존재하는 객체라면, Reachable 상태  
> 유효한 참조가 존재하지 않는 객체라면, Unreachable 상태

Root set과의 관계로 객체의 상태를 판단한다.
> Root set이란 Stack 영역 지역 변수와 파라미터, Method 영역의 정적 변수, JNI에 의해 생성된 객체 등을 말한다.

### 1-2 GC 동작 방법

1. Root set으로부터 Heap 영역의 모든 객체를 스캔하여 Reachable한 객체를 찾는다.
2. Unreachable한 객체를 Heap 영역에서 제거한다.

첫 번째 과정을 Reachable한 객체를 찾아서 Marking한다고 하여 `Mark`라고한다.  
두 번째 과정을 Unreachable한 객체를 Heap 영역에서 쓸어내린다고 하여 `Sweep`이라고 한다.  
그래서 GC의 동작 방법은 `Mark And Sweep`이라고 할 수 있다.
> Compact 과정 : Sweep 후에 분산된 객체들을 Heap의 시작 주소로 모아 메모리가 할당된 부분과 그렇지 않은 부분으로 압축한다. (지원하지 않는 GC도 존재)

### 1-3 Heap 영역의 구분

JVM Heap 영역은 Young generation과 Old generation으로 나뉜다.  
그렇다면 왜 Heap 메모리 구조를 나누어 관리할까 ?

1. 하나의 메모리 영역일 때, 발생할 수 있는 문제점

- 모든 객체를 추적하는 것은 많은 시간이 소요될 수 있고, 이는 부하를 발생시킨다.

2. Weak Generational Hypothesis

- 대부분의 할당된 객체는 오랫동안 참조되지 않으며, 금방 Garbage 대상이 된다.
- 오래된 객체에서 젊은 객체로의 참조는 거의 없다.

영역을 나누어 GC가 일부의 메모리 영역만 스캔한다.

- 효율적으로 GC를 처리할 수 있으므로 GC 비용을 줄일 수 있다.

### 1-4 GC는 언제 일어날까 ?

> Young generation에서 일어나는 GC는 Minor GC라고 한다.  
> Old generation에서 일어나는 GC는 Major GC라고 한다.

Eden : 새로운 객체가 저장되는 영역  
Survivor : Eden 영역에서 살아남은 객체가 저장되는 영역

1. 새로운 객체는 Eden 영역에 할당된다.
2. Eden 영역이 가득차면, Minor GC가 발생한다.

> Mark And Sweep 과정이 일어나고, Unreachable한 객체를 해제한다.

3. 살아남은 객체는 비어있는 Survivor 영역으로 옮겨지고 age가 1 증가한다. (Stop and Copy)

> 1, 2, 3 과정을 반복한다.  
> 단편화 문제를 해결하기 위해 비어있는 Survivor 영역 위주로 옮겨진다.

4. age가 특정값 이상이 되면, Old generation으로 이동한다.

> HotSpot JVM Default 임계값 : 31

5. Old generation 영역이 가득차면, Major GC가 발생한다.

## 2. GC의 종류

### 2-1. Parallel GC

- Java 8의 Default GC
- Minor GC는 Mark-Sweep, Major GC는 Mark-Sweep-Compact를 사용한다.
- Minor GC를 멀티 쓰레드로 수행한다.
- Serial GC에 비해 stop-the-world 시간이 감소한다.
- Parallel GC를 개선한 Parallel Old GC가 존재하고, Major GC도 멀티 쓰레드로 수행한다.

> `Serial GC` : 서버의 CPU 코어가 1개일 때 사용하기 위해 개발된 가장 단순한 GC  
> `stop-the-world` : GC를 수행하기 위해 JVM이 프로그램 실행을 멈추는 현상이다.
> 다른 동작을 멈추기 때문에 오버헤드가 발생할 수 있다. 따라서 이 시간을 최소화하는 것이 중요하다.

### 2-2. CMS GC

- Application 쓰레드와 GC 쓰레드가 동시에 실행되어 stop-the-world 시간을 최대한 줄이기 위해 고안된 GC
- GC 대상을 파악하는 과정과 전체 로직이 복잡하기 때문에 GC 대비 CPU 사용량이 높다.
- Java9부터 deprecated 되었고 Java14에서는 사용이 금지됐다.

### 2-3. G1 GC (Garbage First)

- CMS GC를 대체하기 위해 jdk 7버전에서 최초로 release된 GC
- Java 9+ 버전의 Default GC로 지정되어 있다.
- 기존 GC 알고리즘은 Heap 영역을 물리적으로 고정된 Young/Old 영역으로 나눴다.  
  G1 GC는 Region이라는 개념을 도입해서, Heap 영역을 체스판 같이 분할한다.  
  상황에 맞는 역할을 동적으로 부여하기 때문에 Garbage로 가득찬 영역을 빠르게 회수하여 빈 공간을 확보한다.  
  GC 빈도가 줄어드는 효과를 얻을 수 있다.

> `G1 GC의 효율성`  
> G1 GC에서는 이전의 GC들처럼 일일이 메모리를 탐색해 객체들을 제거하지 않는다.  
> 메모리가 많이 차있는 영역(Region)을 우선적으로 탐색해서 GC한다.  
> G1 GC는 Heap 영역 전체를 탐색하지 않고 Region을 나눠 탐색하고 Region 별로 GC가 일어난다.  
> Young에서 Old로 순차적으로 이동하지 않고 더 효율적이라고 생각하는 위치로 객체를 재할당한다.  
> 예를 들어, Survivor1 영역에 있는 객체가 Eden 영역으로 할당하는 것이 효율적이라고 판단되면 재할당한다.
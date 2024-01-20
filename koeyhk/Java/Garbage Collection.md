## Garbage Collection(GC)

<img src="https://github.com/98000001/CS-Study/assets/80199502/8b88936b-34f5-46c1-838e-39fc33a96cf2"  width="400">

- 자바의 메모리 관리 방법 중 하나
- JVM의 Heap 영역에서 동적으로 할당했던 메모리 중 필요없게 된 메모리 객체(garbage)를 모아 주기적으로 제거하는 프로세스
- 대상 - Unreachable: 객체가 참조되고 있지 않은 상태 (GC의 대상)
- 메모리가 언제 해제되는지 정확하게 알 수 없어 제어하기 힘들며, 가비지 컬렉션(GC)이 동작하는 동안에는 다른 동작을 멈추기 때문에 오버헤드가 발생되는 문제점 → Stop The World


### Stop The World (STW)

- GC를 수행하기 위해 JVM이 프로그램 실행을 멈추는 현상
- GC가 작동하는 동안 GC 관련 Thread를 제외한 모든 Thread는 멈추게 되어 서비스 이용에 차질이 생길 수 있음

### Garbage Collection 청소 방식

- Mark 과정: 먼저 Root Space로부터 그래프 순회를 토앻 연결된 객체들을 찾아내어 각각 어떤 객체를 참조하고 있는지 찾아서 마킹
- Sweep 과정: 참조하고 있지 않은 객체, 즉 Unreachable 객체들을 Heap에서 제거
- Compact 과정: Sweep 후에 분산된 객체들을 Heap의 시작 주소로 모아 메모리가 할당된 부분과 그렇지 않은 부분으로 압축

<br>

## JVM GC 동작 과정

<img src="https://github.com/98000001/CS-Study/assets/80199502/ca397b44-cb47-4657-bfeb-68bf146e7135"  width="700">

### Heap 메모리 구조

<img src="https://github.com/98000001/CS-Study/assets/80199502/3c913aea-253a-4953-b08f-9d82ba0f7ca8"  width="700">

### Young 영역(Young Generation)

- 새롭게 생성된 객체가 할당되는 영역
- 대부분의 객체가 금방 Unreachable 상태가 되기 때문에, 많은 객체가 Young 영역에 생성되었다가 사라짐
- Young 영역에 대한 가비지 컬렉션(Garbage Collection)을 Minor GC라고 부른다.
- 효율적인 GC를 위해 3가지 영역으로 나눔
    - Eden: new를 통해 새로 생성된 객체가 위치, GC 후 살아남은 객체들은 Survivor 영역으로 보냄
    - Survivor 0 / Survivor 1: 최소 1번의 GC 이상 살아남은 객체가 존재하는 영역, 0 or 1 둘 중 하나는 꼭 비어 있어야 함

### Old 영역(Old Generation)

- Young영역에서 Reachable 상태를 유지하여 살아남은 객체가 복사되는 영역
- Young 영역보다 크게 할당되며, 영역의 크기가 큰 만큼 가비지는 적게 발생
- Old 영역에 대한 가비지 컬렉션(Garbage Collection)을 Major GC 또는 Full GC라고 부른다.

<br>

### Minor GC 과정
Young Generation 영역에서 발생되는 GC

<img src="https://github.com/98000001/CS-Study/assets/80199502/bd4a521e-bb28-4e74-8316-990c8a87b5b1"  width="600">

1. Minor GC는 Eden 영역이 가득 찬 후 실행
2. Eden 영역에서 참조가 남아있는 객체를 mark하고 survivor 영역으로 복사, Eden 영역을 비움
3. Survivor 영역도 가득차면 같은 방식으로 다른 Survivor 영역에 복사하고 비움
4. 이를 반복하다 보면 계속해서 살아남는 객체는 old 영역으로 이동

<br>

### ****Major GC 과정****
Old Generation은 길게 살아남는 메모리들이 존재하는 공간으로 이 영역에서 발생되는 GC
**Stop-The-World** 문제가 발생

<img src="https://github.com/98000001/CS-Study/assets/80199502/bb3f3c94-c990-4638-ab61-931d782399c1"  width="600">

1. Old 영역은 데이터가 가득 차면 GC를 실행
2. 삭제되어야 하는 객체를 mark하고 지움(sweep) 
3. 메모리는 단편화된 상태이므로 이를 한 군데에 모아주는 것을 Compaction이라 하며 compact라함 (Mark-Sweep-Compact 알고리즘)

<br>

## Garbage Collection 알고리즘

### Serial GC (-XX:+UseSerialGC)

<img src="https://github.com/98000001/CS-Study/assets/80199502/48cceb8e-8623-46fe-931a-12160832d9f3"  width="300">

- 가장 단순한 방식의 GC로 싱글 스레드(스레드 1개)로 동작
- 싱글 스레드로 동작하여 느리고, 그만큼 Stop The World 시간이 다른 GC에 비해 길다.
- Mark & Sweep & Compact 알고리즘 사용
- 보통 실무에서 사용하는 경우는 없음 (디바이스 성능이 안좋아서 CPU 코어가 1개인 경우에만 사용)

<br>

### Parallel GC (-XX:+UseParallelGC)

<img src="https://github.com/98000001/CS-Study/assets/80199502/b692ec2e-1510-4505-a93c-5c5d957d1489"  width="300">

- Java 8의 default GC
- Young 영역의 GC를 멀티 스레드 방식을 사용하기 때문에, Serial GC에 비해 상대적으로 Stop The World가 짧음 (Old 영역은 아님)

<br>

### Parallel Old GC (-XX:+UseParallelOldGC / -XX:+ParallelGCThreads=n)

<img src="https://github.com/98000001/CS-Study/assets/80199502/14cd3017-0ae6-40cb-9399-e7dd72ca8e5d"  width="500">

- Parallel GC는 Young 영역에 대해서만 멀티 스레드 방식을 사용했다면, Parallel Old GC는 Old 영역까지 멀티스레드 방식을 사용
- 새로운 가비지 컬렉션 청소 방식인 Mark-Summary-Compact 방식을 이용 (Old 영역도 멀티 쓰레드로 처리)

<br>

### CMS GC(Concurrent Mark Sweep GC)

<img src="https://github.com/98000001/CS-Study/assets/80199502/ba3ef07b-a68a-49f6-904f-dac5fecdfa47"  width="700">

- Stop The World로 Java Application이 멈추는 현상을 줄이고자 만든 GC
- GC 대상을 파악하는 과정이 복잡한 여러단계로 수행되기 때문에 다른 GC 대비 CPU 사용량이 높음
- 메모리 파편화 문제

<br>

### G1 GC (Garbage Frist GC) (-XX:+UseG1GC)

<img src="https://github.com/98000001/CS-Study/assets/80199502/a8eb198b-4a5e-4ab6-82f0-30e34a86f1af"  width="800">

- Java 9+의 default GC
- 현재 GC 중  Stop The World의 시간이 제일 짧음
- CMS GC를 개선하여 만든 GC로 위에서 살펴본 GC와는 다른 구조를 가짐
- Heap을 Region이라는 일정한 부분으로 동적으로 나눠서 메모리 관리
- Garbage로 가득찬 영역을 빠르게 회수하여 빈 공간을 확보하므로, 결국 GC 빈도가 줄어드는 효과를 얻게 되는 원리 (메모리가 많이 차있는 영역을 우선적으로 GC)
- Heap Memory 전체를 탐색하는 것이 아닌 영역(region)을 나눠 탐색하고 영역(region)별로 GC

<br>

### Shenandoah GC

<img src="https://github.com/98000001/CS-Study/assets/80199502/f7e60ab2-0012-4845-bf92-e57927d25763"  width="800">

- Java 12에 release
- 레드 햇에서 개발한 GC
- 기존 CMS가 가진 단편화, G1이 가진 pause의 이슈를 해결
- 강력한 Concurrency와 가벼운 GC 로직으로 heap 사이즈에 영향을 받지 않고 일정한 pause 시간이 소요가 특징

<br>

### ****ZGC (Z Garbage Collector)****

<img src="https://github.com/98000001/CS-Study/assets/80199502/26ca4918-766a-4eb0-9c52-d98459b1ce13"  width="500">

- Java 15에 release
- 대량의 메모리(8MB ~ 16TB)를 low-latency로 잘 처리하기 위해 디자인 된 GC
- G1의 Region 처럼, ZGC는 ZPage라는 영역을 사용하며, G1의 Region은 크기가 고정인데 비해, ZPage는 2mb 배수로 동적으로 운영됨 (큰 객체가 들어오면 2^ 로 영역을 구성해서 처리)
- ZGC가 내세우는 최대 장점 중 하나는 힙 크기가 증가하더도 'stop-the-world'의 시간이 절대 10ms를 넘지 않는다는 것

<br>
<br><br><br><br><br><br>

참고 자료: https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EA%B0%80%EB%B9%84%EC%A7%80-%EC%BB%AC%EB%A0%89%EC%85%98GC-%EB%8F%99%EC%9E%91-%EC%9B%90%EB%A6%AC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98-%F0%9F%92%AF-%EC%B4%9D%EC%A0%95%EB%A6%AC

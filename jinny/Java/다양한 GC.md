## GC 종류
STW (Stop The World)GC를 수행하기 위해 JVM이 프로그램 실행을 멈추는 현상을 의미.
GC가 작동하는 동안 GC 관련 Thread를 제외한 모든 Thread는 멈춤

#### Stop-The-World 
자동으로 처리해준다 해도 메모리가 언제 해제되는지 정확하게 알 수 없어 제어하기 힘들며, 가비지 컬렉션(GC)이 동작하는 동안에는 다른 동작을 멈추기 때문에 오버헤드가 발생되는 문제점

![image](https://github.com/98000001/CS-Study/assets/96863137/25c629a5-b627-4e65-8e3b-c84e64c8db03)

### Serial GC
- CPU 코어가 1개일 때 사용하기 위해 개발됨
- GC를 처리하는 쓰레드가 1개 (싱글 쓰레드), 가장 stop-the-world 시간이 김
- Minor GC 에는 Mark-Sweep을 사용하고, Major GC에는 Mark-Sweep-Compact를 사용

### Parallel GC 
- Serial GC와 기본적인 알고리즘은 같지만, Young 영역의 Minor GC를 멀티 쓰레드로 수행 (Old 영역은 여전히 싱글 쓰레드)
- Serial GC에 비해 stop-the-world 시간 감소

![image](https://github.com/98000001/CS-Study/assets/96863137/8e27168c-4053-47b0-9c0e-fb105ebef8c5)

### Parallel Old GC
- Young 영역 뿐만 아니라, Old 영역에서도 멀티 쓰레드로 GC 수행
- 새로운 가비지 컬렉션 청소 방식인 Mark-Summary-Compact 방식을 이용 

### CMS GC
- 어플리케이션의 쓰레드와 GC 쓰레드가 동시에 실행되어 stop-the-world 시간을 최대한 줄이기 위해 고안된 GC
- GC 대상을 파악하는 과정이 복잡한 여러단계로 수행되기 때문에 다른 GC 대비 CPU 사용량이 높다
- 메모리 파편화 문제
  
### G1 GC
- CMS GC를 대체하기 위해 jdk 7 버전에서 최초로 release된 GC
- 기존의 GC 알고리즘에서는 Heap 영역을 물리적으로 고정된 Young / Old 영역으로 나누어 사용하였지만, G1 gc는 아예 이러한 개념을 뒤엎는 Region이라는 개념을 새로 도입
- 전체 Heap 영역을 Region이라는 영역으로 체스같이 분할하여 상황에 따라 Eden, Survivor, Old 등 역할을 고정이 아닌 동적으로 부여
- Garbage로 가득찬 영역을 빠르게 회수하여 빈 공간을 확보하므로, 결국 GC 빈도가 줄어드는 효과를 얻게 되는 원리

### Shenandoah GC
- 기존 CMS가 가진 단편화, G1이 가진 pause의 이슈를 해결
- 강력한 Concurrency와 가벼운 GC 로직으로 heap 사이즈에 영향을 받지 않고 일정한 pause 시간이 소요가 특징

### ZGC 
- 대량의 메모리(8MB ~ 16TB)를 low-latency로 잘 처리하기 위해 디자인 된 GC
- G1의 Region 처럼,  ZGC는 ZPage라는 영역을 사용하며, G1의 Region은 크기가 고정인데 비해, ZPage는 2mb 배수로 동적으로 운영됨
- ZGC가 내세우는 최대 장점 중 하나는 힙 크기가 증가하더도 'stop-the-world'의 시간이 절대 10ms를 넘지 않는다는 것



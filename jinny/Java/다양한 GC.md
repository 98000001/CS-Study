## GC 종류
STW (Stop The World)GC를 수행하기 위해 JVM이 프로그램 실행을 멈추는 현상을 의미.
GC가 작동하는 동안 GC 관련 Thread를 제외한 모든 Thread는 멈춤

### Serial GC
- CPU 코어가 1개일 때 사용하기 위해 개발됨
- GC를 처리하는 쓰레드가 1개 (싱글 쓰레드), 가장 stop-the-world 시간이 김

## CountDownLatch vs CyclicBarrier
CyclicBarrier 는 여러 쓰레드가 서로를 기다리고 CountDownLatch 는 하나 또는 다수의 쓰레드가 작업이 완료될 때 까지 기다림

### CountDownLatch
원하는 지점에서 await() 메서드를 호출해서 코드의 진행을 중단시키고, 다른 스레드들에서 원하는 횟수만큼 countDown() 메서드를 호출해주면 그때 비로소 코드가 진행되게 됨

'''
CountDownLatch countDownLatch = new CountDownLatch(3);
  IntStream.range(0, 5)
    .mapToObj(i -> new Worker(i, countDownLatch))
    .map(Thread::new)
    .forEach(Thread::start);

countDownLatch.await(); // 실행되는 쓰레드 (여기선 메인이라고 하자) 가 다른 쓰레드에서 countDown 이 3번 호출 될 때 까지 기다린다.
'''

### CyclicBarrier
모든 스레드들이 대기상태에 빠진다. 그리고 조건을 충족할때 모든 스레드들이 대기에서 해제
CyclicBarrier 모든 스레드들이 Barrier Point 에 도착하는 것을 보장해야 할 때 사용

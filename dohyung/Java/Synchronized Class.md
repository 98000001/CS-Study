## 1. Synchronized Class

JDK 1.5에 추가된 concurrent 패키지에서는 동기화 클래스들을 제공한다.  
이 클래스를 통해 멀티 스레드 환경에서 안전한 코드를 작성할 수 있다.

### 1-1. CountDownLatch

Latch의 사전적 의미는 걸쇠이다.  
원하는 지점에서 await() 메서드를 호출하고 코드의 진행을 중단시킨다.  
다른 스레드에서 설정한 횟수만큼 countDown() 메서드를 호출하면 다시 코드를 진행한다.  
await() 메서드는 timeout을 매개변수로 받기 때문에 timeout을 설정하면 횟수만큼 호출이 안되더라도 설정한 시간 이후에 코드가 다시 진행된다.

### 1-2. Semaphore

세마포어는 permits의 수를 설정하고 acquire() 메서드를 통해 하나씩 호출한다.  
호출했을 때 permits의 수를 초과하면 해당 스레드는 대기 상태가 된다.  
tryAcquire() 메서드를 이용하면 permits를 획득했는지 boolean 타입으로 리턴한다.  
release() 메서드를 통해 permits을 반환할 수 있다.
세마포어를 이용하여 컬렉션의 사이즈를 제한하는 작업을 할 수 있다.

### 1-3. CyclicBarrier

CyclicBarrier는 CountDownLatch와 비슷하다.  
CountDownLatch는 await()를 호출한 스레드만 대기 상태가 되고 countDown()을 호출한 스레드는 대기 상태가 되지 않는다.  
즉, await()를 호출한 스레드가 영영 대기 상태에 빠지더라도 countDown()을 호출하는 스레드들은 자기 할 일을 계속한다.
CyclicBarrier는 작업에 참여하는 모든 스레드들이 대기 상태에 빠진다.  
그리고 조건을 충족했을 때 모든 스레드들이 대기 상태에서 해제된다.
## **CountDownLatch**

- 원하는 지점에서 await() 메서드를 호출해서(걸쇠를 걸어서) 코드의 진행을 중단시키고, 다른 스레드들에서 원하는 횟수만큼 countDown() 메서드를 호출해주면 그때 비로소 코드가 진행
- CountDownLatch 는 await() 을 호출한 스레드만 대기상태가 되고, countDown() 을 호출하는 다른 스레드들은 countDown() 메서드와 무관하게 대기상태에 빠지지 않음

```java
public static void main(String[] args) throws Exception {              
    CountDownLatch countDownLatch = new CountDownLatch(5);             
                                                                       
    ExecutorService es = Executors.newFixedThreadPool(5);              
    for(int i = 0; i < 5; i++) {                                       
        int n = i;                                                     
        es.execute(() -> {                                             
            countDownLatch.countDown();                                
            System.out.println("order :: " + n);                       
        });                                                            
    }                                                                  
                                                                       
    countDownLatch.await();                                            
    es.shutdown();                                                     
    System.out.println("finish");
}         
```

- 메인 스레드에서 await() 메서드를 호출해서 코드를 중단시키고 5개의 스레드를 생성해 각각 countDown() 메서드를 호출. countDown() 메서드가 5번 호출되지않으면 await() 아래의 코드는 실행되지 않음

<br>

## **CyclicBarrier**

- CyclicBarrier 는 해당 장벽에 참여하는 모든 스레드들이 대기상태에 빠짐
- 조건을 충족할때 모든 스레드들이 대기에서 해제

```java
public static void main(String[] args) throws Exception {           
    CyclicBarrier cyclicBarrier = new CyclicBarrier(5);             
                                                                    
    ExecutorService es = Executors.newFixedThreadPool(4);           
    for(int i = 0; i < 4; i++) {                                    
        int n = i;                                                  
        es.submit(() -> {                                           
            cyclicBarrier.await();                                  
            System.out.println("order :: " + n);                    
            return 1;                                               
        });                                                         
    }                                                               
                                                                    
    Thread.sleep(5000);                                             
    cyclicBarrier.await();                                          
                                                                    
    es.shutdown();                                                  
    System.out.println("finish");                                   
}                
```

- 메인스레드까지 await() 을 호출하고나서야 모든 출력이 정상적으로 이루어짐


<br><br><br><br><br>

참고 자료: <br>
https://multifrontgarden.tistory.com/266

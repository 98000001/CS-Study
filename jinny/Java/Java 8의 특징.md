## Lambda expression(람다 표현식)
메서드로 전달할 수 있는 Anonymous function(익명 함수)를 단순한 문법으로 표기

```
Thread thread = new Thread(new Runnable() {
    @Override
    public void run() {
        System.out.println("Start to new thread!");
    }
});// 익명 클래스로 Runnalbe을 구현
thread.start();
```

```
Thread thread = new Thread(() -> System.out.println("Start to new thread!"));// 람다 표현식으로 단순하게 표현
```

## Functional interface(함수형 인터페이스)
단 하나의 추상 메서드를 갖는 인터페이스를 함수형 인터페이스 (static 함수는 여러 개 가질 수 있습니다.)

## Default method(디폴트 메서드)
Java 8 에서는 메소드 선언 시에 default를 명시하게 되면 인터페이스 내부에서도 로직이 포함된 메소드를 선언 가능해짐
이를 통해서 '하위 호환성'을 유지하고 인터페이스의 보완 가능


이외에도 

java.time 패키지: 더 직관적이고 개선된 Date, Time API를 제공
나즈혼 (Nashorn): 자바스크립트의 새로운 엔진을 도입 

등등...

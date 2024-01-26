1. Lambda expression(람다 표현식)
메서드로 전달할 수 있는 Anonymous function(익명 함수)를 단순한 문법으로 표기

// 익명 클래스로 Runnalbe을 구현
Thread thread = new Thread(new Runnable() {
    @Override
    public void run() {
        System.out.println("Start to new thread!");
    }
});

thread.start();

// 람다 표현식으로 단순하게 표현
Thread thread = new Thread(() -> System.out.println("Start to new thread!"));
        
thread.start();

2. Functional interface(함수형 인터페이스)
단 하나의 추상 메서드를 갖는 인터페이스를 함수형 인터페이스 (static 함수는 여러 개 가질 수 있습니다.)

3.Default method(디폴트 메서드)

public interface Car {
	// 전진
	void drive();
    
    // 후진
    void reverse();
    
    // 날기 
    default void fly() {
    	System.out.println("Fly");
    }
}

 Java 8 에서는 메소드 선언 시에 default를 명시하게 되면 인터페이스 내부에서도 로직이 포함된 메소드를 선언 가능해짐
 이를 통해서 '하위 호환성'을 유지하고 인터페이스의 보완 가능

default method의 필요성
인터페이스에 추상메서드를 추가하게 되면 모든 구현체에 구현을 해야함
=>인터페이스에 default method를 사용하면 추가 변경을 막을 수 있다. 

개방 폐쇄 원칙 (OCP : Open Close Principle)

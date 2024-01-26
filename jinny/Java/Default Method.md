#### 기존 Interface의 문제점
![image](https://github.com/98000001/CS-Study/assets/96863137/85defdce-4a81-47d6-a384-f06aff84f8ef)
ClassA, ClassB, ClassC에 모두 methodA 를 구현 -> 근데 만약 ClassA ~ Z 라면?
![image](https://github.com/98000001/CS-Study/assets/96863137/3887e03a-3290-4925-a83c-517ebcc4e50c)
InterfaceA의 구현체 클래스에 추가되는 메서드 methodA를 구현을 26개 해줘야함
말이 안됨~!!

#### 개방 폐쇄 원칙 (OCP : Open Close Principle)
소프트웨어 구성 요소(컴포넌트, 클래스, 모듈, 함수)는 확장에 대해서는 개방(OPEN)되어야 하지만 변경에 대해서는 폐쇄(CLOSE)되어야 한다는 의미
## 확장은 할 수 있지만(OPEN) 변경에 대한 폐쇄(CLOSE)를 위반한 케이스

# Default Method
인터페이스에 추상메서드를 추가하게 되면 모든 구현체에 구현을 해야한다.
## => 인터페이스에 default method를 사용하면 추가 변경을 막을 수 있다.
이로써 OCP(Open-Close-Principle : 개방 폐쇄 원칙) 에서 확장에 개방(Open)되어 있고, 변경에 닫혀(Close)있는 코드를 설계할 수 있게됨

- 여러 인터페이스의 default 메소드 간의 충돌 : 구현한 클래스에서 디폴트 메소드를 오버라이딩 하기.
- default 메소드와 부모 클래스의 method 간의 충돌 : 부모 클래스의 메소그가 상속되고, default 메소드는 무시

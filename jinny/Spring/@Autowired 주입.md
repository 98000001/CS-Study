## 생성자 vs Setter

1. 생성자 방식(constructor-based injection)
   – Bean의 생성자(constructor)를 통해 의존 객체를 주입
   – 이용가능한 생성자가 bean 클래스에 정의되어야 함
2. Setter method 방식 (setter-based injection)
   – Property에 대한 setter method를 통해 의존 객체 주입
   – Bean class에 property에 대한 setter method가 정의되어 있어야 함

생성자 방식
   – Bean 객체를 생성하는 시점에 모든 의존 객체가 주입됨
   – 성능상 유리하고, 객체를 사용하기 전에 필요한 의존 객체가 모두 주입된 상태이므로 NullPointerException 발생 가능성 낮음 
   – 생성자의 인자들의 순서대로 적합한 의존 객체를 전달해야 함 인자가 많을 경우 어떤 필드에 어떤 의존 객체를 주입하는지 파악하기 어려움

Setter method 방식 
   – 생성자를 통해 bean 객체가 생성된 후 의존 객체가 주입됨
   – setter method를 통해 각 필드마다 필요한 의존 객체를 주입하므로 설정이 명확하고 용이함
   – setter들을 별도로 실행하므로 성능이 다소 저하되고, setter의 실행이 누락된 경우 해당 객체 참조 시 NullPointerException 발생 가능


필드 주입
필드 주입(Field Injection)은 필드에 바로 의존 관계를 주입하는 방법


## 권장
생성자를 통한 주입
1. 순환 참조 방지
개발을 하다 보면 여러 컴포넌트 간에 의존성이 생김
생성자를 통해 주입하고 실행하면 BeanCurrentlyInCreationException이 발생
순환 참조 뿐만아니라 더 나아가서 의존 관계에 내용을 외부로 노출 시킴으로써 어플리케이션을 실행하는 시점에서 오류를 체크할 수 있음

2.불변성(Immutability
세터랑 필드는 OOP의 5가지 원칙 중 OCP(Open-Closed Principal, 개방-폐쇄의 원칙)를 위반
생성자 주입을 통해 변경의 가능성을 배제하고 불변성을 보장하는 것이 좋음


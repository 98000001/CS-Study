# @ Autowired 주입 방법별 차이(Field, Setter, Constructor Injection)

## DI (Dependency Injection)

- 각 클래스간 의존 관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결
- 의존성 주입 ; 필요한 객체를 직접 생성하는 것이 아닌 외부로부터 객체를 받아서 사용하는 것
    - 객체간 결합도 줄이고, 의존성 줄이고 코드의 재활용성 높일 수 있음
    - test 가 용이해짐

### Field Injection

- 필드에 @Autowired
    - 코드가 간결하지만 외부에서 변경하기 힘듦
    - 프레임워크에 의존적이고 객체지향적으로 좋지 않음

### Setter Injection

- Setter 메소드에 @Autowired
- 수정자 주입은 set 메소드를 public 으로 열어두어야하기에 언제 어디서든 변경 가능하기에 안좋음

### **Constructor Injection (Best!)**

- 클래스 생성자가 하나이고 그 생성자로 주입받을 객체가 빈으로 등록되어있을 때.
- 생성자 주입을 권장하는 이유
    - Field Injection 의 단점
        - Field Injection 이 편리하고 코드가 간결하다는 장점이 있지만, 외부에서 수정이 불가능하고 테스트 코드 작성 시 객체 수정할 수 없음
    - Setter Injection 의 단점
        - Setter를 public으로 구현할 경우 관계 주입 받는 객체의 변경 가능성이 열려있음. 변경 가능성을 열어두면 다른 곳에서 임의로 객체 변경 할 수있기에 에러 발생 할 수 있음
    - 순환 참조 방지
        - 필드 주입과 수정자 주입은 빈이 생성된 후 참조하기에 애플리케이션이 아무 오류, 경고 없이 구동 → 실제 코드가 호출될 때까지 문제를 알 수 없음
        - 생성자를 통해 주입하고 실생하면 BeanCurrecntlyInCreationException 발생
    - 불변성
        - 생성자로 의존성 주입시 final 선언할 수 있고 이를 통해 런타임에서 의존성 주입받은 객체가 변할 일이 없어짐. 하지만 수정자, 필드 주입시 불필요한 수정 가능성을 열어두게 되고, OCP를 위반.
        - 변경 가능성 배제, 불변성 보장
        - 필드 주입은 null 이 될 가능성이 있는데 final로 선언한 생성자 주입은 null이 불가능
    - 테스트에 용이함
        - 독립적 인스턴스가 가능한 POJO를 사용하면 DI 컨테이너 없이도 의존성 주입해 사용 가능
        - 코드의 가독성이 높아지며 유지보수에 용이
- Lombok의 @RequiredArgsConstructor
    - 클래스에 선언된 final 변수들, 필드들을 매개변수로 하는 생성자를 자동으로 생성해줌
    - Constructor Injection 에 해당
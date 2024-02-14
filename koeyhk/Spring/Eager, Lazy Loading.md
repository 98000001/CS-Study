# Eager, Lazy Loading

### Fetch Type

- JPA가 Entity를 조회할 때, 연관관계에 있는 객체들을 어떻게 가져올 것이냐를 나타내는 설정값
- JPA는 ORM기술로 객체와 필드를 보고 쿼리를 생성함 → 다른 객체와 연관관계 매핑이 되어있으면 그 객체들까지 조회하는데 어떻게 불러올 것인지 설정하는 것

<br>

### Eager Loading (즉시 로딩)

- 특정 엔티티를 조회할 때 연관된 모든 객체의 데이터를 한 번에 불러옴
- 실무에서 엔티티 간의 관계가 복잡할수록 join으로 인한 성능 저하와 N+1 문제 발생
- @xxxToxxx(fetch = fetchType.EAGER)

<br>

### Lazy Loading (지연 로딩)

- 필요한 시점에 연관된 객체를 불러옴
- @xxxtoxxx(fetch = fetchType.LAZY)
- 연관된 엔티티를 조회하기 위해 연관 관계에 있는 변수에 '프록시 객체'를 넣어둠. 그리고 실제 데이터가 필요한 순간에 호출하여 DB를 조회해서 프록시 객체를 초기화

<br>

### **JPA 기본 fetch 전략**

- @ManyToOne : EAGER
- @OneToOne : EAGER
- @ManyToMany : LAZY
- @OneToMany : LAZY

## 1. Collection Framework

Java에서 Collection이란 데이터의 집합, 그룹을 의미한다.  
Java Collection Framework는 객체들을 한 곳에 모아 관리하고, 편하게 사용하기 위해 제공되는 환경이다.  
데이터와 자료구조인 컬렉션과 이를 구현하는 클래스를 정의하는 인터페이스를 제공한다.  
Collection에는 List, Map, Set, Stack, Queue 등이 존재한다.

### 1-1. Collection의 용도

- 다수의 데이터를 다루는 표준화된 클래스들을 제공해주기 때문에 자료구조를 직접 구현하지 않고 편하게 사용할 수 있다.
- 배열과 다르게 객체를 보관하기 위한 공간을 미리 정하지 않아도 되므로, 공간을 동적으로 사용할 수 있다.

### 1-2. Collection Framework의 상속 구조

Collection 인터페이스는 크게 List, Set, Queue로 세 가지 상위 인터페이스로 분류할 수 있다.  
그리고 Map은 Collection 인터페이스를 상속받고 있지 않지만 Collection으로 분류된다.

| 인터페이스 | 구현 클래스                                    | 특징                                                                           |
|-------|-------------------------------------------|------------------------------------------------------------------------------|
| Set   | HashSet  <br/>  TreeSet                   | 순서를 유지하지 않는 데이터의 집합으로 중복을 허용하지 않는다.                                          |
| List  | LinkedList  <br/> Vector  <br/> ArrayList | 순서가 있는 데이터의 집합으로 데이터의 중복을 허용한다.                                              |
| Map   | HashMap  <br/>  HashTable  <br/>  TreeMap | (키, 값)의 쌍으로 이루어진 데이터의 집합으로 순서는 유지되지 않는다.  <br/> 키의 중복을 허용하지 않으나 값의 중복은 허용한다. |
| Queue | LinkedList  <br/> PriorityQueue           | List와 유사                                                                     |
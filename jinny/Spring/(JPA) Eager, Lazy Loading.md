## Fetch Type 
참조하는 객체들의 데이터를 가져오는 시점을 정할 수 있음
- Eager 즉시로딩
  데이터를 가져올 때 하나의 객체만 가져오는 것이 아닌 참조 객체들의 데이터까지 전부 읽어오는 방식
  조인으로 인한 성능 저하를 피할 수 없고 JPQL에서 N+1문제
- Lazy
  참조 객체들의 데이터들은 무시하고 해당 엔티티의 데이터만 가져오는 방식

default
  OneToMany Lazy
  ManyToMany Lazy
  ManyToOne Eager
  OneToOne Eager

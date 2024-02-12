# JPA와 Hibernate

### JPA(Java Persistent API)

- 자바 ORM(Object Relational Mapping) 기술에 대한 API 표준 명세
- JPA는 특정 기능을 하는 라이브러리가 아닌, ORM을 사용하기 위한 인터페이스를 모아둔 것
- 자바 어플리케이션에서 관계형 데이터베이스를 어떻게 사용해야 하는지를 정의하는 방법중 한 가지
- JPA를 사용하기 위해서는 JPA를 구현한 Hibernate, EclipseLink, DataNucleus 같은 ORM 프레임워크를 사용해야 함

<img src="https://github.com/98000001/CS-Study/assets/80199502/3a219874-f704-43e5-b168-3cdae5bd7df7"  width="600">

<br>

### Hibernate

<img src="https://github.com/98000001/CS-Study/assets/80199502/10e5e80d-52c8-4895-a000-3b8df6fed790"  width="600">

- JPA의 구현체 중 하나
- SQL을 사용하지 않고 직관적인 코드(메소드)를 사용해 데이터를 조작 가능
- Hibernate가 지원하는 메소드 내부에서는 JDBC API가 동작하고 있으며, 단지 개발자가 직접 SQL을 작성하지 않을 뿐임
- JPA와 Hibernate는 마치 자바의 interface와 해당 interface를 구현한 class와 같은 관계

<img src="https://github.com/98000001/CS-Study/assets/80199502/75af65a3-29ab-4b20-952f-a09030b1d4c4"  width="600">

- JPA와 Hibernate의 상속 및 구현 관계를 나타낸 것
- JPA의 핵심인 EntityManagerFactory, EntityManager, EntityTransaction을Hibernate에서는 각각 SessionFactory, Session, Transaction으로 상속받고 각각 Impl로 구현하고 있음을 확인할 수 있음

### Hibernate의 장점

- 생산성: SQL을 직접 사용하지 않고, 메소드 호출만으로 query가 수행됨
- 유지보수: JPA가 여러 일들을 대신 해주기 때문에 유지보수 측면에서 좋음
- 객체지향적 개발: 비즈니스 로직에 집중 가능
- 특정 벤더에 종속적이지 않음: 추상화된 데이터 접근 계층을 제공

<br>

### Spring Data JPA

- Spring에서 제공하는 모듈 중 하나로 JPA를 쉽고 편하게 사용할 수 있도록 도와줌
- JPA를 사용하려면 EntityManager를 주입받아 사용해야 하지만, Spring Data JPA는 JPA를 한단계 더 추상화 시킨 Repository 인터페이스를 제공

### Hibernate와 Spring Data JPA의 차이점

- 하이버네이트는 JPA 구현체
- Spring Data JPA는 JPA에 대한 데이터 접근의 추상화로 항상 Hibernate와 같은 JPA 구현체가 필요함

<br><br><br><br><br>

참고 자료: <br>
https://dev-coco.tistory.com/74

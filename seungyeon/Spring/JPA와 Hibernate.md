# JPA와 Hibernate

### SQL Mapper

- SQL ← mapping → Object
- SQL 문으로 직접 디비를 조작한다
    - Mybatis, jdbcTemplate

### ORM

- DB 데이터 ← mapping → Object
- 객체와 DB 데이터를 자동으로 매핑해준다
    - 객체간 관계를 바탕으로 SQL을 자동으로 생성한다
    - JPA,Hibernate

### JPA = 기술 명세

- 자바 애플리케이션에서 RDB를 사용하는 방식을 정의한 인터페이스.
- 특정 기능을 하는 라이브러리가 아니라, 자바 애플리케이션에서 RDB를 어떻게 사용해야하는지 정의하는 방법.
- JPA는 단순 명세이기에 구현이 없음.
- 개발자가 JPA를 사용하면 JPA 내부에서 JDBC API를 사용해 SQL을 호출해 DB와 통신함.
- ORM 이기 때문에 자바 클래스와 DB 테이블을 매핑한다 (sql을 매핑하지 않음)
    - ORM 을 위한 자바 EE 표준

### Hibernate =  JPA의 구현체

- EntityManager 와 같은 인터페이스를 직접 구현한 라이브러리.
- JPA와 Hibernate는 자바의 Interface와 interface 구현한 class 와 같은 관계
- JPA를 사용하기 위해 Hibernate를 사용할 필요가 없다. 대체 가능.

### Spring Data JPA = JPA를 편하게 만들어놓은 모듈

- Spring에서 제공하는 모듈 중 하나로 JPA를 더 쉽고 편하게 사용할 수 있도록 해줌
- JPA를 추상화시킨 Repository 인터페이스를 제공한다
- Repository 인터페이스에 정해진 규칙대로 메소드를 입력하면 Spring이 알아서 적합한 쿼리를 날리는 구현체를 만들어 Bean에 등록한다
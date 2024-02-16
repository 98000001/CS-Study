## JPA
### JPA는 객체-관계 매핑(ORM)을 위한 표준 명세인 인터페이스
JPA는 특정 기능을 하는 라이브러리가 아닌 인터페이스
내부적으로 JPA는 JDBC API를 사용하여 데이터베이스와 상호작용

<img width="529" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/a8108a8e-0d9f-4528-ad7f-51bda32a9091">

## Hibernate
### Hibernate는 JPA의 구현체
Hibernate는 객체와 관계형 데이터베이스 간의 매핑을 자동으로 처리해서 개발자가 일일이 SQL 쿼리를 작성하지 않도록 도와줌
JPA 를 사용하기 위해서 반드시 Hibernate 를 사용할 필요는 없당

## Spring Data JPA
Spring Data JPA는 Spring에서 제공하는 모듈 중 하나로,  Repository라는 인터페이스를 제공해서 개발자가 JPA를 더 쉽게 사용할 수 있도록 도와준당
Hibernate와 같은 구현체들을 좀 더 쉽게 사용할 수 있도록 추상화한 것.
<img width="708" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/dddaafb7-8957-4e9d-823f-ee8f44db8fa7">

<img width="458" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/4fa12338-0eec-4fab-b04a-e1cdecceb833">

### Hibernate가 JPA 인터페이스를 준수하는 구현이고, Spring Data JPA가 유용하게 사용할 수 있게끔 하는 모듈이자 프레임워크인 것이다.

+ Querydsl은 HQL(Hibernate Query Language) 쿼리를 Type-Safe하게 유지보수해야 할 필요로 탄생
+ Querydsl은 타입 세이프한 SQL 쿼리형태를 자바 코드로 작성할 수 있게 해주는 프레임워크

  <img width="374" alt="image" src="https://github.com/98000001/CS-Study/assets/96863137/4df21ad4-30c7-48d7-9935-5d23171c16d9">

## mybatis(SQL Mapper) vs spring data jpa(ORM)

### mybatis(SQL Mapper)
- Object와 SQL의 필드를 매핑하여 데이터를 객체화 하는 기술
- 객체와 테이블 간의 관계를 매핑하는 것이 아님
- SQL문을 직접 작성하고 쿼리 수행 결과를 어떠한 객체에 매핑할지 바인딩 하는 방법
- DBMS에 종속적인 문제
- 데이터 캐싱 기능으로 성능 향상
- but 객체와 쿼리문 모두 관리해야함, CRUD 메소드를 직접 다 구현해야함.
  
### spring data jpa(ORM)
- 대표적인 오픈소스로 Hibernate
- CRUD 메소드 기본 제공
- 쿼리를 만들지 않아도 됨
- 1차 캐싱, 쓰기지연, 변경감지, 지연로딩 제공
- MyBatis는 쿼리가 수정되어 데이터 정보가 바뀌면 그에 사용 되고 있던 DTO와 함께 수정해주어야 하는 반면에,
JPA 는 객체만 바꾸면 된다. 즉, 객체 중심으로 개발 가능
- but 복잡한 쿼리는 해결이 어려움

객체와 테이블의 차이

객체 두 개로 다대다 관계 가능
정규화된 테이블 두 개로 다대다 관계를 표현불가 -> 연결 테이블을 추가해서 일대다 - 다대일 관계로 풀어내야함

단방향
@ManyToMany 어노테이션을 사용하여 다대다 관계를 매핑
@JoinTable: 연결 테이블 지정

양방향
양방향 관계를 위한 mappedBy 속성

한계와 극복
컬럼을 추가하면 더는 @ManyToMany를 사용 할 수 없음
#### 왜냐하면 새로 추가될 컬럼들은 엔티티에 매핑할 수 없기 때문
=> 연결 테이블을 엔티티로 취급
다대다 관계를 일대다 - 다대일 관계으로 변경

# N:M 관계

### 다대다 매핑의 한계

- 연결 테이블이 단순히 연결만 하고 끝나지 않음
    - 조인 테이블 자체에 주문시간, 수량 같은 추가 데이터가 많이 들어갈 수 있지만, 매핑 정보만 넣는 것이 가능하고, 추가 정보를 넣는 것 자체가 불가능
    - 중간 테이블이 숨겨져 있기 때문에 예상하지 못하는 쿼리들이 나감
    - 이런 이유들로 실무에서 사용하면 안 됨

### 다대다 매핑의 한계 극복

- 연결 테이블용 엔티티를 추가
    - @ManyToMany를 @ManyToOne, 다대일 관계 두개로 풀어냄

<img src="https://github.com/98000001/CS-Study/assets/80199502/0e075b43-cd8a-42de-8356-043fed81fb30" width=700>

<br><br><br>
<br><br>

참고 자료: <br>
https://ict-nroo.tistory.com/127 <br>
[https://learnote-dev.com/java/Spring-다대다-관계-맵핑/](https://learnote-dev.com/java/Spring-%EB%8B%A4%EB%8C%80%EB%8B%A4-%EA%B4%80%EA%B3%84-%EB%A7%B5%ED%95%91/)

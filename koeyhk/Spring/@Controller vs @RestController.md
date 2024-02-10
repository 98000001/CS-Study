# @Controller vs @RestController

## @Controller

### **View 반환**

<img src="https://github.com/98000001/CS-Study/assets/80199502/6bb06468-d1ee-4a96-8f31-02e41ac29ff9"  width="400">

- **주로 View를 반환하기 위해 사용**
- `ViewResolver`가 적절한 View를 찾아서 렌더링해서 반환

### **Data 반환**

<img src="https://github.com/98000001/CS-Study/assets/80199502/d2ced15b-9a26-442e-8598-6c1e86bb38a1"  width="400">

- `@ResponseBody` 어노테이션을 사용하면 View 말고 직접 Data를 반환시켜줄 수 있다.
- HTTP 요청을 객체로 변환하거나, 객체를 응답으로 변환하는 `HttpMessageConverter`를 사용
- 하지만 헤더를 유연하게 설정할 수 없음

<br>

## **@RestController**

<img src="https://github.com/98000001/CS-Study/assets/80199502/2afdac64-c48c-4a3a-96e6-27bc5a40309c"  width="400">

- `@RestController` 를 붙이면 모든 메서드에서는 `@ResponseBody` 어노테이션이 기본으로 작동
- Json 형태로 객체 데이터 반환
- `@RestController` 가 Data를 반환하기 위해서는 `viewResolver` 대신에 `HttpMessageConverter`가 동작
    - 단순 문자열일 경우 `StringHttpMessageConverter` 사용
    - 객체인 경우 `MappingJackson2HttpMessageConverter` 사용


<br><br><br>

참고 자료: <br>
https://www.nowwatersblog.com/springboot/springstudy/trivial

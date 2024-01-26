### Stream API
1. 외부 반복을 통해 작업하는 컬렉션과는 달리 내부 반복(internal iteration)을 통해 작업을 수행
2. 스트림은 재사용이 가능한 컬렉션과는 달리 단 한 번만 사용
3. 스트림은 원본 데이터를 변경X
4. 스트림의 연산은 필터-맵(filter-map) 기반의 API를 사용하여 지연(lazy) 연산을 통해 성능을 최적화
5. 스트림은 parallelStream() 메소드를 통한 손쉬운 병렬 처리를 지원합니다.

### 스트림 API의 동작 흐름
1. 스트림의 생성
2. 스트림의 중개 연산 (스트림의 변환)
3. 스트림의 최종 연산 (스트림의 사용)

![image](https://github.com/98000001/CS-Study/assets/96863137/185ef673-6924-4cc2-b910-9f4185cd8839)

### 스트림의 생성
- 컬렉션
  Collection 인터페이스에는 stream() 메소드가 정의
  -> List와 Set 컬렉션 클래스에서도 stream() 메소드로 스트림을 생성
  parallelStream() 메소드를 사용하면 병렬 처리가 가능한 스트림을 생성
- 배열
  Arrays 클래스에는 다양한 형태의 stream() 메소드가 클래스 메소드로 정의
- 가변 매개변수
  Stream 클래스의 of() 메소드를 사용하면 가변 매개변수(variable parameter)를 전달받아 스트림을 생성
- 지정된 범위의 연속된 정수
  IntStream나 LongStream 인터페이스에는 range()와 rangeClosed() 메소드가 정의
- 특정 타입의 난수들
- 람다 표현식
  무한 스트림을 생성하기 위해 Stream 클래스에는 iterate()와 generate() 메소드가 정의 
- 파일
  파일의 한 행(line)을 요소로 하는 스트림을 생성하기 위해 java.nio.file.Files 클래스에는 lines() 메소드가 정의 
- 빈 스트림

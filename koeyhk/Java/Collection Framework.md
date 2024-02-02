# Collection Framework

- 일정 타입 데이터들을 처리하기 위해 정의되어 있는 표준화된 클래스 및 인터페이스의 집합

<img src="https://github.com/98000001/CS-Study/assets/80199502/a79c73f8-2e00-43ea-9341-582a8a16e345"  width="800">

### **List 인터페이스 (순서 O, 중복 O)**

- 선형 자료구조를 가지고 있어데이터가 연속적/순차적으로(ordered) 저장
- 연속적으로 객체를 저장하기 때문에 배열과 마찬가지로 인덱스를 통해 객체를 추가/수정/삭제/검색 가능
- 중복을 허용하기 때문에, 같은 값을 저장할 수 있음

```
List<String> list = new ArrayList<>();
List<String> list = new LinkedList<>();
```

<br>

### **Set 인터페이스 (순서X, 중복X)**

- 순서가 없기 때문에 인덱스로 접근이 불가하며 객체에 접근하기 위해서는 iterator 을 사용
- 객체를 중복해서 저장할 수 없음

```
HashSet<String> hashSet = new HashSet<>();
```

<br>

### Map 인터페이스 (순서X, 중복 키 X / 중복 데이터 O)

- <키(Key),값(Value)> 형식을 가지고 있는 인터페이스
- 비순차적, 키 값은 중복을 허용하지 않음

```
HashMap<String , String> map = new HashMap<String , String>();
```

<br><br><br><br><br>

참고 자료: <br>
https://life-with-coding.tistory.com/491 <br>
https://coding-factory.tistory.com/550

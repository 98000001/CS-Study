# Hash

- 내부적으로 배열을 사용하여 데이터를 저장하기 때문에 빠른 검색속도
- 데이터 추가/삭제시 기존 데이터를 밀어내거나 당기는 작업이 필요없도록 데이터와 연관된 고유한 숫자를 만들어 낸 뒤 이를 인덱스로 사용

<br>

### Hash Table

- 컬렉션 프레임웍이 만들어지기 이전부터 존재하던 것
- HashMap과 사용법 거의 동일
- `Thread-safe`, key에 null을 허용하지 않음, Enumeration을 제공

<br>

### HashMap

- 데이터를 저장할 때 키(Key)와 밸류(Value)가 짝을 이루어 저장
- key - value 형태이고 key는 중복될 수 없고, value는 중복될 수 있음
- 데이터의 추가, 삭제, 특히 검색이 빠름
- `Thread-safe`하지 않음, key에 null을 허용, Enumeration을 제공하지 않음, 보조해시를 사용해 충돌이 덜 발생가능
- ex. {'a': 1, 'b': 1, 'c': 2}

```
HashMap<String, String> h1 = new HashMap<String, String>( );
```

<br>

### HashSet

- 객체 그 자체를 저장
- 중복된 값을 허용하지 않고, 저장한 순서가 보장되지 않음
- ex. {'a', 'b', 'c'}

```java
HashSet<String> a = new HashSet<String>();
HashSet<String> b = new HashSet<>();
```

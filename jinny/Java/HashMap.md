## 해시(Hash) 
HashTable은 HashMap의 구버전
HashMap은 Map의 구현체
Map의 특징인 키(key), 값(value)을 묶어서 하나의 데이터(entry)로 저장
해싱을 사용하기 때문에 많은 양의 데이터를 검색하는데 있어서 뛰어난 성능

### 충돌
서로 다른 두 개의 키가, 해쉬 함수를 통과하였는데, 그 결과가 같다면 => 충돌
충돌이 많이 일어난다면, O(1)으로 값을 탐색할 수 있는 장점이 없어진다

충돌 문제 해결책
1. Open Addressing
해시 충돌이 발생하면, 비어 있는 다른 칸에 저장하는 방식
바로 옆이 비어있다면 거기 넣을 수도 있고, 따로 함수를 만들어 다른 곳에 넣을 수도 있다

3. Separate Chaining
Java에서는 Separate Chaining 방식을 사용하여 HashMap 을 구현하고 있다. Separate Chaining 방식으로는 두 가지 구현 방식이 존재한다.

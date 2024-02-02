## 1. Hash

Hash는 단방향 암호화 기법은 Hash Function을 이용해서 생성된 고정된 길이의 비트를 의미한다.  
해시 함수는 주어진 입력 데이터를 고정된 길이의 해시 값으로 매핑한다.

### 1-1. HashMap, HashTable

해시 함수를 사용하여 키를 해시값을 매핑하고, 이 해시값을 색인(index) 또는 주소로 설정한다.  
이런 키와 데이터 값을 함께 저장하는 자료구조를 HashMap, HashTable이라고 한다.  
이때 데이터가 저장된 공간을 버킷 또는 슬롯이라고 한다.

### 1-2. Java에서의 차이

Java에서 HashMap과 HashTable의 가장 큰 차이는 Thread-Safe다.  
HashTable의 모든 데이터 변경 메서드는 Synchronized로 설정돼 있다.  
즉, 메서드 호출 전 동기화 잠금을 통해 멀티 스레드 환경에서 데이터의 무결성을 보장한다.  
하지만 HashMap은 Thread-Safe 하지 않아서 멀티 스레드 환경에서 동시에 데이터를 조작하면 데이터에 문제가 발생할 수 있다.

HashTable은 Collection Framework가 등장하기 전부터 존재한 오래된 자료구조라 느리다.  
그래서 ConcurrentHashMap을 쓰는 것이 권장된다.
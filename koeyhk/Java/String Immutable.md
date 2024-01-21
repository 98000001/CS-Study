## String Immutable(String constant pool, "a" vs new String("a"))

- Java에서 String은 불변(Immutable) → String은 기본 타입이 아닌 참조 타입 (Reference Type)
- **Java에서 String 객체는 특별히 String constant pool에서 따로 관리가 됨**

<br>

### Java에서 String이 Immutable 한 이유

- **캐싱** - JVM이 String Constant Pool 이라는 영역을 만들고 문자열들을 Constant화하여 다른 변수 혹은 객체들과 공유하게 되는데, 이 과정에서 데이터 캐싱이 일어나고 그만큼 성능적 이득을 취함
- **동기화** - Multi-Thread 환경에서 동기화 문제가 발생하지 않기 때문에 더욱 안전한 결과를 냄
- **보안적 이유** - Mutable 하다면 특정 공격 벡터에 의해 일관성한 데이터가 아니게 될 수 있다.

<br>

### **String Constant Pool**

Java에서 문자열 리터럴을 저장하는 독립된 영역

<img src="https://github.com/98000001/CS-Study/assets/80199502/991287f7-07d1-48db-a427-03f6cd2c2749"  width="700">

- String 은 재사용될 확률이 높기 때문에 Heap 영역 내에 문자열 상수의 Pool 을 유지하고 해당 Pool 로 사용자가 정의한, 변수가 가지고 있는 value 들을 담음
- Constant Pool이 있어 String value 들이 Immutable 한 특성을 가지게 됨
- 한번 저장된 문자열은 소스코드에서 동일한 문자열에 대해 재사용하여 메모리를 절약하는 역할을 함
- 리터럴("Hello")로 선언된 문자열이 이 저장공간에 저장되며, 동적으로 생성된 문자열은 저장되지 않음
- new 연산자로 생성한 String 객체는 같은 값이 String Pool에 이미 존재하더라도, Heap 영역 내 별도의 객체를 가리키게 됨

```java
String str = "hello"; // String constant pool에 저장
String str2 = "hello"; // String constant pool에서 재사용
String str3 = new ("hello"); // 별도의 Heap 메모리에 저장

System.out.println(str == str2);	// true (같은 객체를 재사용하기 때문에)
System.out.println(str == str3);	// false
System.out.println(str.equals(str3));	// true
```

String a = new String("hello"); // 1. new 키워드로 생성하기

String b = "hello"; // 2. 리터럴로 생성하기

String a = new String("hello");
String b = "hello"; 
String c = "hello";

// == , equals() 두 가지 방법으로 비교해보기
System.out.print("(1) " + a.equals(b)); // true
System.out.print("(2) " + a == b); // false
System.out.print("(3) " + b == c); // true



## new 키워드
new로 객체가 생성이 되면 해당 객체는 Heap 영역에 값이 위치하게 됩니다.
보통 객체가 생성되는 원리와 유사합니다.

## String 리터럴(Literal)
문자열 리터럴을 이용하여 생성하는 방식입니다.
리터럴을 String 레퍼런스에 바로 넣어줍니다.
String Constant Pool 이라는 공간에 값이 생성됩니다.
명칭 그대로 문자열들을 저장해놓은 Pool

### String 연산하기
String 객체는 기본적으로 불변(immutable)객체
여러 객체가 Pool에 있는 같은 String을 참조하기때문에 String은 immutable
String에 값을 변경하려고 한다면 객체의 값이 변경되는것이 아니라 기존 객체는 유지되고 새로운 객체가 생성

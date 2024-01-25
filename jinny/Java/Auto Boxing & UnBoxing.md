### primitive Data
boolean, char, byte, short, int, long, float, double
가벼운 데이터
스택 메모리에 위치
### Object Date
무거운 데이터
실제 데이터는 힙메모리에 공유하고 래퍼런스만 스택메모리에 위치


### Wrapper Class
primitive Data를 객체로 다루기 위해서 사용하는 Class
primitive Data를 ObjectDate화 시킨 Class

#### 래퍼 클래스 사용 이유
재네릭, 자료구조, 매개변수 등 기본 자료형이 아닌 래퍼런스 타입을 필요로 하는 경우가 많고 메서드를 갖고 있어 다양하게 활용 가능
인스턴스를 생성하여 상속 및 재사용 가능
문자열(String)을 기본 타입 값으로 변환할 때

### 래퍼 클래스 종류

![image](https://github.com/98000001/CS-Study/assets/96863137/3c39f289-a6dd-4f6a-ba05-3bceb1b7b165)

## autoboxing
primitive Date에서 Wrapper Class로 자동으로 변환되는 것
가벼운 데이터를 무거운 데이터에 넣기
컴파일러가 primitive Date 를 Object Date로 자동변환 하는 것
기본타입의 값을 포장객체로 만드는 과정
래퍼 클래스에 기본 자료형의 데이터 대입

## auto unboxing
Wrapper Class에서 primitive Date으로 자동으로 변환 되는 것
컴파일러가 Object Data를 primitive Date로 자동변환 하는 것
무거운 데이터를 가벼운 데이터에 넣기
포장객체에서 기본타입의 값을 얻어내는 과정
기본 자료형에 래퍼 객체 대입

![image](https://github.com/98000001/CS-Study/assets/96863137/fea7097b-e7c6-4a06-8c9a-f180a00938a1)

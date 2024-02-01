## Reflection
객체를 통해 클래스의 정보를 분석해내는 프로그램 기법
- 기본적으로 제공하는 자바의 API
- 자바의 Reflection은 클래스, 인터페이스, 메서드들을 찾을 수 있고, 객체를 생성하거나 변수를 변경할 수 있고, 메서드도 가능

### Reflection 얻는 방법
class.forName("path/Person")
인스턴스 person.getClass()
Person.class

받을 때 Type은 Class<? extends Person
Reflection객체 -> 클래스의 내부 정보 꺼내기 
- getFields(
- getDeclaredFields()
- getDeclaredMethods()

## Annotation 
비지니스 로직과 다른 부가적인 로직들의 분리를 위해(AOP)
@Override 상속받은 클래스의 메서드를 오버라이딩 어노테이션
@Deprecated같은 경우 더이상 사용되지 않는 문법으로 사용하지 않은것을 권장하는 어노테이션

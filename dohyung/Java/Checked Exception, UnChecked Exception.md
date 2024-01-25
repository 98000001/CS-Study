## 1. Checked Exception, UnChecked Exception

Exception도 두 가지 종류로 나뉜다.
> Checked Exception : 컴파일 예외 클래스들  
> UnChecked Exception : 런타임 예외 클래스들

컴파일/런타임 예외로 분류하지 않고, 위와 같이 분류했다.  
코드적 관점에서 예외 처리 동작을 필수 지정 유무에 따라 나뉘기 때문이다.

|       |                          Checked Exception                          |                  UnChecked Exception                  | 
|:-----:|:-------------------------------------------------------------------:|:-----------------------------------------------------:|
| 처리 여부 |                            반드시 예외 처리가 필요                            |                   명시적인 예외 처리가 필요 없음                   |
| 확인 시점 |                               컴파일 단계                                |                        런타임 단계                         |
| 예외 종류 | RuntimeException 클래스 제외<br/>Exception 클래스<br/>Exception를 상속받는 하위 예외 | RuntimeException 클래스<br/>RuntimeException를 상속받는 하위 예외 |

## 2. 분류에 따른 예외 처리 유무

Checked/UnChecked Exception의 핵심적인 차이는 예외 처리의 필요성이다.  
Checked Exception은 확인하는 시점이 컴파일 단계여서 별도의 예외 처리가 없다면 컴파일 자체가 되지 않는다.  
따라서 반드시 로직을 `try-catch`로 감싸거나 `throws`로 예외를 던져야 한다.

- IOException
- FileNotFoundException
- SQLException

반면에 UnChecked Exception은 명시적인 예외처리가 필요 없다.  
당연히 예외지만 개발자의 충분한 주의로 미리 회피할 수 있다.  
또한 미약한 예외로 처리되어 Java 컴파일러는 별도의 예외 처리를 하지 않도록 설계되어있다.

- NullPointerException
- IllegalArgumentException
- IndexOutOfBoundException
- SystemException

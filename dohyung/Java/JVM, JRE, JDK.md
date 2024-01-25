## 1. JVM, JRE, JDK

### 1-1 JVM (Java Virtual Machine)

Java 코드를 실행하기 위한 가상머신이다.

- Java 프로그램이 기기나 운영체제에 상관없이 어디서든 실행될 수 있도록 해준다. (WORA 원칙)
> `WORA` : `Write Once, Run Anywhere`의 줄임말이고 한 번 쓰고 모든 곳에서 실행된다.라는 뜻이다.
- Java 프로그램의 메모리를 효율적으로 관리 & 최적화한다.
> JVM은 GC를 사용해서 메모리를 관리한다.

### 1-2 JRE (Java Runtime Environment)

JVM은 우리가 작성한 코드를 기반으로 .class 확장자를 가진 클래스 파일이 작동할 수 있도록 환경을 제공해준다.  
하지만 원활하게 작동하기 위해서는 필수적인 요소들이 더 필요하다.  
이를 제공해주는 것이 JRE(Java Runtime Environment)다.  
JRE는 크게 JVM, Java Class Libraries, Class Loader로 구성된다.

> `Java Class Libraries`는 java.io, java.util, java.thread 등 작동에 필수적인 요소들을 가지고 있다.

간단한 코드라도 필수 라이브러리가 필요하다.  
Class Loader는 필요한 클래스들을 JVM 위로 올려주는 역할을 한다.
JRE의 구성요소들을 통해서, JVM은 원활히 작동할 수 있다.
하지만 JRE는 개발에 사용되는 것이 아닌 구동시키는 데 집중하고 있다.
Java 코드가 주어져도 이를 분석하거나 클래스 파일로 변환하는 일은 할 수 없다.
Java Compiler를 비롯한 개발에 필요한 요소들이 개발을 하기 위해서 더 필요하다.

### 1-3 JDK (Java Development Kit)

Java를 활용하여 프로그램을 개발할 때 필요한 도구 모음이다.  
실제로 프로그램을 실행해야 하기 때문에 JRE를 포함한다.  
JDK는 대표적으로 다음과 같은 기능을 추가로 가진다.
- Java로 이루어진 코드를 클래스 파일로 컴파일하는 javac의 기능
- 작성한 코드를 디버깅하는 jdb 기능

JDK에서는 개발과 실행에 필요한 환경 및 기능 제공의 폭에 따라 표준형인 SE, 여러 기능이 추가된 EE로 나뉜다.  
이런 구분 이외에도 출시된 순서에 따라서 숫자로 버전을 구분하는 방법도 있다.
> `SE` : Standard Edition  
> `EE` : Enterprise Edition
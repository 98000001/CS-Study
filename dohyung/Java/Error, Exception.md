## 1. Error, Exception

### 1-1. Error

Error는 시스템이 종료되어야 할 수준의 상황과 같은 수습하기 힘든 심각한 문제를 의미한다.  
개발자가 미리 예측하여 대처하기 힘들다.

- OutOfMemoryError : JVM에 설정된 메모리의 한계를 넘었을 때 발생한다.

### 1-2. Exception

Exception은 개발자가 구현한 로직에서 발생한 문제나 사용자에 의해 발생한 문제를 의미한다.  
Error와 달리 다소 심각하지 않은 오류이며, 개발자가 미리 예측하여 방지할 수 있다.  
상황에 맞는 적절한 예외처리(Exception Handler)가 필요하다.

### 1-3. Exception Handling

Exception Handling은 프로그램 실행 시 발생할 수 있는 예기치 못한 예외에 대비하는 것이다.  
Error는 어쩔 수 없지만, Exception은 개발자가 충분히 포괄적으로 방지할 수 있기 때문이다.  
예외 처리의 목적은 예외가 발생해도 프로그램의 비정상 종료를 막고 정상적인 실행 상태를 유지하는 것이다.

### 1-4. Throwable Class

Error와 Exception 모두 Java의 최상위 클래스인 Object를 상속받는다.  
그리고 그 사이에 Throwable Class와 상속 관계가 있고, 오류나 예외에 대한 메시지를 가지고 있다.  
대표적으로 getMessage(), printStackTrace() 메서드가 이 Class에 속해 있다.
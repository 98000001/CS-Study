### 제네릭(generic)이란 
데이터의 타입(data type)을 일반화한다(generalize)는 것을 의미
클래스나 메소드에서 사용할 내부 데이터 타입을 컴파일 시에 미리 지정하는 방법
  1. 클래스나 메소드 내부에서 사용되는 객체의 타입 안정성을 높일 수 있
  2. 반환값에 대한 타입 변환 및 타입 검사에 들어가는 노력을 줄일 수 있음

![image](https://github.com/98000001/CS-Study/assets/96863137/b915bd06-b68a-464e-b06e-095ddc0d1d0e)

### 제네릭의 선언 및 생성
예제) 
```

class MyArray<T> {

    T element;

    void setElement(T element) { this.element = element; }

    T getElement() { return element; }

}

```
위와 같이 선언된 제네릭 클래스(generic class)를 생성할 때에는 타입 변수 자리에 사용할 실제 타입을 명시해야 하고
래퍼(wrapper) 클래스를 사용.
```

MyArray<Integer> myArr = new MyArray<Integer>();

```

### 제네릭의 제거 시기
사용된 제네릭 타입은 컴파일 시 컴파일러에 의해 자동으로 검사되어 타입 변환됨 -> 코드 내의 모든 제네릭 타입은 제거되어, 컴파일된 class 파일에는 어떠한 제네릭 타입도 포함되지 않음

### 제한된 Generic(제네릭)

특정 범위 내로 좁혀서 제한하고 싶다면 -> extends 와 super, ?

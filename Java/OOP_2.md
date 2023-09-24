# 객체지향 프로그래밍

## 상속(inheritance)

### 상속의 정의와 장점

- 상속이란, 기존의 클래스를 재사용하여 새로운 클래스를 작성하는 것이다
  - 보다 적은 양의 코드로 새로운 클래스를 작성할 수 있다
  - 코드를 공통적으로 간리할 수 있기 때문에 코드의 추가 및 변경이 매우 용이하다
    - 이러한 특징은 코드의 재사용성을 높이고 코드의 중복을 제거하여 프로그램의 생산성과 유지보수에 크게 기여한다
- 자바에서 상속을 구현하는 방법
  - 새로 작성하고자 하는 클래스의 이름 뒤에 상속받고자 하는 클래스의 이름을 키워드 'extends'와 함께 써주기만 하면 된다

```java
class Parent { }
class Child extends Parent {
    // ...
}
```

- 새로 작성하려는 클래스의 이름이 Child이고 상속받고자 하는 기존 클래스의 이름이 Parent인 경우
- 이 두 클래스는 서로 상속 관계에있다고 한다
- 상속해주는 클래스를 '조상 클래스'라 하고 상속받는 클래스를 '자손 클래스'라고 한다

```java
조상 클래스 : 부모(parent)클래스, 상위(super)클래스, 기반(base)클래스
자손 클래스 : 자식(chile)클래스, 하위(sub)클래스, 파생된(derived)클래스
```

- 클래스 Parent와 Child의 상속 관계도 <br>
  ![상속관계도](https://github.com/nohheeyeon/TIL/assets/130336617/2cbc6d0b-cc04-422b-a36f-5e2915bfec09)
  - 프로그램이 커질 수록 클래스 간의 관계가 복잡해지는데, 이 때 상속관계도로 표현하면 클래스 간의 관계를 보다 쉽게 이해할 수 있습니다
- 클래스 Parent와 Child의 다이어그램 <br>
  ![다이어그램](https://github.com/nohheeyeon/TIL/assets/130336617/3a3bf8e3-f2a4-4060-8af9-beea7a144e5c)
  - 자손 클래스는 조상 클래스의 모든 멤버를 상속받기 때문에, Child클래스는 Parent클래스의 멤버들을 포함한다고 할 수 있다
  - 클래스는 멤버들의 집합이므로 클래스 Parent와 Child의 관계를 다이어그램같이 표현할 수도 있다
- Parent클래스에 age라는 정수형 변수를 멤버변수로 추가
  - 자손인 Child 클래스에 새로운 멤버로 play() 메서드를 추가 <br>
    ![image](https://github.com/nohheeyeon/TIL/assets/130336617/49d6a67e-2206-4c0e-bf9a-2e917df9e1b7)

```java
class Parent {
    int age;
}

class Child extends Parent {
    void play() {
        SSystem.out.println("놀자~");
    }
}
```

- 자손 클래스는 조상의 멤버를 모두 상속받기 때문에, Child클래스는 자동적으로 age라는 멤버변수가 추가된 것과 같은 효과를 얻는다
- Child클래스에 새로운 코드가 추가되어도 조상인 Parent클래스느 아마ㅜ런 영향도 받지 않는다
  - 조상 클래스가 변경되면 자손 클래스는 자동적으로 영향을 받게 되지만, 자손 클래스가 변경되는 것은 조상 클래스에 아무런 영향을 주지 못 한다
- 자손 클래스는 조상 클래스의 모든 멤버를 상속 받으므로 항상 조상 클래습돠 같거나 많은 멤버를 갖는다
- 상속에 상속을 거듭할수록 상속받는 클래스의 멤버 개수는 점점 늘어나게 도니다
  - 상속을 받는다는 것은 조상 클래스를 확장(extend)한다는 의미로 해석할 수도 있으며 이 것이 상속에 사용되는 키워드가 'extends'인 이유이기도 하다

```java
* 생성자와 초기화 블럭은 상속되지 않는다. 멤버만 상속된다
* 자손 클래스의 멤버 개수는 조상 클래스보다 항상 같거나 같다
```

### 클래스 간의 관계 - 포함관계

- 클래스를 재사용하는 방법
  - 클래스 간에 '포함(Composite)' 관계를 맺어주는 것이다
    - 클래스 간의 포함관계를 맺어주는 것은 한 클래스의 멤버변수로 다른 클래스 타입의 참조변수를 선언하는 것을 뜻한다

```java
class Circle {
    int x; // 원점의 x좌표
    int y; // 원점의 y좌표
    int r; // 반지름(radius)
}
```

- 좌표 상의 한 점을 다루기 위한 Point 클래스

```java
class Point {
    int x; // x좌표
    int y; // y좌표
}
```

- Point클래스를 재사용해서 Circle클래스를 작성한다면!

```java
class Circle {
    Point c = new Point(); // 원점
    int r;
}
```

- 한 클래스를 작성하는데 다른 클래스를 멤버변수로 선언하여 포함시키는 것은 좋은 생각이다
  - 하나의 거대한 클래스를 작성하는 것 보다 단위별로 여러 개의 클래스를 작성한 다음, 이 단위 클래스들을 포함관계로 재사용하면 보다 간결하고 손쉬벡 클래스를 작성할 수 있다

### 클래스간의 관계 결정하기

- 클래스를 작성하는데 있어서 상속관계를 맺어 줄 것인지 포함관계를 맺어 줄 것인 지 결정하는 것은 때때로 혼돈스러울 수 있다
- '~은 ~이다(is-a)'와 '~은 ~을 가지고 있다(has-a)'를 넣어서 문장을 만들어보면 클래스 간의 관계다 보다 명확해 진다

```java
원(Circle)은 점(Point)이다. - Circle is a Point. // 상속관계
원(Circle)은 점(Point)을 가지고 있다. - Circle has a Point. // 포함관계
```

### 단일상속(single inheritance)

- 자바에서는 단일 상속만을 허용한다
  - 둘 이상의 클래스로부터 상속을 받을 수 없다

```java
class TvDVD extends Tv, DVD { // 에러, 조상은 하나만 허용된다
    // ...
}
```

- 다중상속을 허용하면 여러 클래스로부터 상속받을 수 있기 때문에 복합적인 기능ㅇ르 가진 클래스를 쉽게 작성할 수 있다는 장점이 있지만, 클래스간의 관계가 매우 복잡해진다는 것과 서로 다른 클래스로부터 상속받은 멤버 간의 이름이 같ㅇ느 경우 구별할 수 있는 방법이 없다는 단점을 가지고 있다
- 단일 상속이 하나의 조상 클래스만을 가질 수 있기 때문에 다중상속에 비해 불편한 점도 있지만, 클래스 간의 관계가 보다 명확해지고 코드를 더욱 신뢰할 수 있게 만들어 준다는 점에서 다중상속보다 유리하다

### Object클래스 - 모든 클래스의 조상

- 모든 클래스 상속계층도의 최상위에 있는 조상클래스이다
  - 다른 클래스로부터 상속받지 안ㅇㅎ는 모든 클래스들은자동적으로 Object클래스로부터 상속받게 함으로써 이것을 가능하게 한다

```java
class Tv {
  ...
}
```

- 컴파일러는 자동적으로 'extends Object'를 추가하여 Tv클래스가 Object클래스로부터 상속받도록 한다
- 만일 다른 클래스로부터 상속을 받는다고 하더라도 상속계층도를 딸 ㅏ조상클래스, 조상클래스의 조상클래스를 찾아 올라가다 보면 결국 마지막 최상위 조상은 Object클래스일 것이다
  - 이미 어떤 클래스로부터 상속받도록 작성된 클래스에 대해서는 컴파일러가 'extends Object'를 추가하지 않는다 <br>
    <img width="300" alt="image" src="https://github.com/nohheeyeon/TIL/assets/130336617/71bda9bb-7e1e-41e0-8815-f6774bfb61ee">

```java
class Tv {
  ...
}

class SmartTv extends Tv {
  ...
}
```

- Tv클래스가 있고, Tv클래스를 상속받는 SmartTv가 있을 때의 상속계층도
  - 상속계층도를 단순화하기 위해서 Object클래스를 생략하는 경우가 많다
- 자바의 모든 클래스들은 Object클래스를 상속받기 때무에 Object클래스에 정의된 멤버들을 사용할 수 있다
  - toString()이나 equals(Object o)와 같은 메서드를 따로 정의하지 않고도 사용할 수 있었던 이유는 이 메서드들이 Object클래스에 정의된 것들이기 때문이다

## 오버라이딩(overriding)

### 오버라이딩이란?

- 조상클래스로부터 상속받은 메서드의 내용을 변경하는 것을 오버라이딩이라고 한다
- 상속받은 메서드를 그대로 사용하기도 하지만, 자손 클래스 자신에 맞게 변경해야하는 경우가 많다
  - 이럴 때 조상의 메서드를 오버라이딩한다

```java
class Vehicle {
  void run() {
              System.out.println("차량이 달립니다.");
    }
}

class Car extends Vehicle {
  @Override
  void run() {
              System.out.println("자동차가 주행합니다.");
    }
}

public class Main {
  public static void main(String[] args) {
              Vehicle vehicle1 = new Vehicle();
              Vehicle vehicle2 = new Car(); // 업캐스팅

              vehicle1.run(); // "차량이 달립니다." 출력
              vehicle2.run(); // "자동차가 주행합니다." 출력
    }
}
```

- Car 클래스는 Vehicle 클래스의 run 메서드를 오버라이딩하여 자체적인 구현을 함
- Vehicle2는 Car 클래스의 인스턴스이지만 Vehicle 타입의 참조변수에 할당되었으며, run 메서드가 Car 클래스의 버전을 실행하게 된다

### 오버라이딩의 조건

- 오버라이딩은 메서드의 내용만을 새로 작성하는 것이므로 메서드의 선어부는 조상의 것과 완전히 일치해야한다

```java
자손 클래스에서 오버라이딩하는 메서드는 조상 클래스의 메서드와
- 이름이 같아야 한다
- 매개변수가 같아야 한다
- 반환타입이 같아야 한다
```

### 오버로딩 vs 오버라이딩

**오버로딩** 기존에 없는 새로운 메서드를 정의하는 것(new)
**오버라이딩** 상속받은 메서드의 내용을 변경하는 것(change, modify)

```java
class Parent {
    void parentMethod() {}
  class Child extends Parent {
        void parentMethod() {}
        void parentMethod(int i) {}

        void childeMethod() {}
        void childeMethod(int i) {}
        void childeMethod() {}
    }
  }
}
```

### super

- super은 자손 클래스에서 조상 클래스로부터 상속받은 멤버를 참조하는데 사용되는 참조 변수이다

### super() - 조상 클래스의 생성자

- this()와 마찬가지고 super() 역시 생성자이다
- this()는 같은 클래스의 다른 생성자를 호출하는데 사용되지만, super()는 조상 클래스의 생성자를 호출하는데 사용된다

## package와 import

## 패키지(package)

### 패키지의 개념

패키지는 자바 코드를 조직화하고 관리하기 위한 방법 중 하나입니다. 코드의 클래스들을 논리적으로 그룹화하여 관리할 수 있습니다. 이렇게 패키지를 사용하면 클래스명의 충돌을 방지하고 코드를 보다 체계적으로 관리할 수 있습니다.

### 패키지의 선언

패키지를 선언하려면 소스 코드 파일의 가장 위에 패키지 선언문을 작성합니다. 패키지 선언문은 다음과 같은 형식을 갖습니다:

```java
package com.example.myproject;
```

위 예제에서 `com.example.myproject`는 패키지의 이름을 나타냅니다. 이 패키지 선언문을 포함하는 클래스 파일은 `com.example.myproject` 패키지에 속하게 됩니다.

### import문

자바에서는 다른 패키지에 속한 클래스를 사용할 때 패키지명을 포함한 전체 클래스 이름을 사용해야 합니다. 그러나 `import`문을 사용하면 특정 클래스를 패키지명 없이 사용할 수 있습니다. 예를 들어:

```java
import java.util.ArrayList;
```

위 코드는 `java.util` 패키지에 속한 `ArrayList` 클래스를 패키지명 없이 사용할 수 있게 해줍니다.

### static import문

`static import`문을 사용하면 다른 클래스의 `static` 멤버(필드 또는 메서드)를 패키지명 없이 사용할 수 있습니다. 예를 들어:

```java
import static java.lang.Math.*;

public class MathTest {
    public static void main(String[] args) {
        double result = sqrt(25.0);
        System.out.println("Square root: " + result);
    }
}
```

위 코드에서 `import static java.lang.Math.*;`는 `Math` 클래스의 모든 `static` 멤버를 패키지명 없이 사용할 수 있게 합니다.

## 제어자(modifier)

### 제어자란?

제어자(modifier)는 클래스, 메서드, 변수 등의 선언부에 추가하여 그 선언부의 속성을 변경하거나 제한하는 역할을 합니다. 제어자를 사용함으로써 코드의 가독성을 높이고 안정성을 유지할 수 있습니다.

### static - 클래스의, 공통적인

`static` 제어자는 클래스의 멤버(필드 또는 메서드)를 공통적으로 사용하기 위해 선언됩니다. 클래스의 인스턴스를 생성하지 않고도 `static` 멤버에 접근할 수 있습니다.

```java
public class MyClass {
    static int staticField; // 정적 필드
    static void staticMethod() { // 정적 메서드
        // ...
    }
}
```

### final - 마지막의, 변경될 수 없는

`final` 제어자는 선언된 필드, 메서드, 클래스를 변경할 수 없게 만듭니다. `final` 필드는 상수로 사용되며, `final` 메서드는 오버라이딩(재정의)할 수 없습니다.

```java
public final class MyFinalClass {
    final int myConstantField = 10; // 상수 필드
    final void myFinalMethod() { // 변경 불가능한 메서드
        // ...
    }
}
```

### abstract - 추상의, 미완성의

`abstract` 제어자는 클래스나 메서드를 추상적으로 선언합니다. 추상 클래스는 객체를 생성할 수 없고, 추상 메서드는 하위 클래스에서 반드시 구현되어야 합니다.

```java
public abstract class MyAbstractClass { // 추상 클래스
    abstract void myAbstractMethod(); // 추상 메서드
}
```

### 접근 제어자(access modifier)

접근 제어자는 클래스, 메서드, 필드 등의 접근 권한을 설정합니다. 자바에서 널

리 사용되는 접근 제어자에는 `public`, `private`, `protected`, 그리고 기본(default) 접근 제어자가 있습니다.

- `public`: 모든 패키지와 클래스에서 접근 가능
- `private`: 같은 클래스 내에서만 접근 가능
- `protected`: 같은 패키지와 하위 클래스에서 접근 가능
- 기본(default): 같은 패키지에서만 접근 가능

### 제어자(modifier)의 조합

제어자는 함께 조합하여 사용할 수 있습니다. 예를 들어, `static`과 `final`을 함께 사용하면 상수(static final)를 선언할 수 있고, `public`과 `abstract`를 함께 사용하면 추상 메서드를 다른 패키지에서도 접근할 수 있게 할 수 있습니다. 조합된 제어자는 해당 멤버의 특성을 더욱 세밀하게 제어합니다.

```java
public static final int MY_CONSTANT = 100; // public, static, final을 조합한 상수 필드
public abstract class MyAbstractClass { // public, abstract를 조합한 추상 클래스
    abstract void myAbstractMethod();
}
```

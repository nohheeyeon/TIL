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
        System.out.println("놀자~");
    }
}
```

- 자손 클래스는 조상의 멤버를 모두 상속받기 때문에, Child클래스는 자동적으로 age라는 멤버변수가 추가된 것과 같은 효과를 얻는다
- Child클래스에 새로운 코드가 추가되어도 조상인 Parent클래스느 아무런 영향도 받지 않는다
  - 조상 클래스가 변경되면 자손 클래스는 자동적으로 영향을 받게 되지만, 자손 클래스가 변경되는 것은 조상 클래스에 아무런 영향을 주지 못 한다
- 자손 클래스는 조상 클래스의 모든 멤버를 상속 받으므로 항상 조상 클래스와 같거나 보다 많은 멤버를 갖는다
- 상속에 상속을 거듭할수록 상속받는 클래스의 멤버 개수는 점점 늘어나게 됩니다
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
  - 하나의 거대한 클래스를 작성하는 것 보다 단위별로 여러 개의 클래스를 작성한 다음, 이 단위 클래스들을 포함관계로 재사용하면 보다 간결하고 손쉽게 클래스를 작성할 수 있다

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

- 다중상속을 허용하면 여러 클래스로부터 상속받을 수 있기 때문에 복합적인 기능을 가진 클래스를 쉽게 작성할 수 있다는 장점이 있지만, 클래스간의 관계가 매우 복잡해진다는 것과 서로 다른 클래스로부터 상속받은 멤버 간의 이름이 같은 경우 구별할 수 있는 방법이 없다는 단점을 가지고 있다
- 단일 상속이 하나의 조상 클래스만을 가질 수 있기 때문에 다중상속에 비해 불편한 점도 있지만, 클래스 간의 관계가 보다 명확해지고 코드를 더욱 신뢰할 수 있게 만들어 준다는 점에서 다중상속보다 유리하다

### Object클래스 - 모든 클래스의 조상

- 모든 클래스 상속계층도의 최상위에 있는 조상클래스이다
  - 다른 클래스로부터 상속받지 않는 모든 클래스들은자동적으로 Object클래스로부터 상속받게 함으로써 이것을 가능하게 한다

```java
class Tv {
  ...
}
```

- 컴파일러는 자동적으로 'extends Object'를 추가하여 Tv클래스가 Object클래스로부터 상속받도록 한다
- 만일 다른 클래스로부터 상속을 받는다고 하더라도 상속계층도를 따라 조상클래스, 조상클래스의 조상클래스를 찾아 올라가다 보면 결국 마지막 최상위 조상은 Object클래스일 것이다
  - 이미 어떤 클래스로부터 상속받도록 작성된 클래스에 대해서는 컴파일러가 'extends Object'를 추가하지 않는다 <br>
    <img width="300" alt="image" src="https://github.com/nohheeyeon/TIL/assets/130336617/71bda9bb-7e1e-41e0-8815-f6774bfb61ee"> <br>

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
- 자바의 모든 클래스들은 Object클래스를 상속받기 때문에 Object클래스에 정의된 멤버들을 사용할 수 있다
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

- 조상 클래스의 메서드를 자손 클래스에서 오버라이딩할 때

1. 선언부가 조상 클래스의 메서드와 일치해야 한다
2. 접근 제어자를 조상 클래스의 메서드보다 좁은 범위로 변경할 수 없다
3. 예외는 조상 클래스의 메서드보다 많이 선언할 수 없다

### 오버로딩 vs 오버라이딩

**오버로딩** 기존에 없는 새로운 메서드를 정의하는 것(new) <br>
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
- 멤버변수와 지역변수의 이름이 같을 때 this를 붙여서 구별했듯이 상속받은 멤버와 자신의 멤버와 이름이 같을 때는 super를 붙여서 구별할 수 있다

### super() - 조상 클래스의 생성자

- this()와 마찬가지고 super() 역시 생성자이다
- this()는 같은 클래스의 다른 생성자를 호출하는데 사용되지만, super()는 조상 클래스의 생성자를 호출하는데 사용된다

## package와 import

## 패키지(package)

### 패키지의 개념

- 패키지란, 클래스의 묶음이다
  - 패키지에는 클래스 또는 인터페이스를 포함시킬 수 있으며, 서로 관련된 클래스들끼리 그룹 단위로 묶어 놓음으로써 클래스를 효율적으로 관리할 수 있다
    - 같은 이름의 클래스 일지라도 서로 다른 패키지에 존재하는 것이 가능하므로, 자신만의 패키지 체계를 유지함으로써 다른 개발자가 개발한 클래스 라이브러리의 클래스와 이름이 충돌하는 것을 피할 수 있다

### 패키지의 선언

- 패키지를 선언하는 것은 클래스나 인터페이스의 소스파일 (.java)의 맨 위에 한 줄만 적어주면 된다

```java
package 패키지명;
```

- 패키지 선언문은 반드시 소스파일에서 주석과 공백을 제외한 첫 번재 문장이어야하며, 하나의 소스파일에 단 한 번만 선언될 수 있다
  - 해당 소스파일에 포함된 모든 클래스나 인터페이스는 선언된 패키지에 속하게 된다
- 패키지명은 대소문자를 모두 허용하지만, 클래스명과 쉽게 구분하기 위해서 소문자로 하는 것을 원칙으로 하고 있다
- 모든 클래스는 반드시 하나의 패키지에 포함되어야하지만, 지금까지 소스파일을 작성할 때 패키지를 선언하지 않고도 아무런 문제가 없었던 이유는 자바에서 기본적으로 제공하는 '이름 없는 패키지(unnamed package)' 때문이다

### import문

- import문의 역할은 컴파일러에게 소스파일에 사용된 클래스의 패키지에 대한 정보를 제공하는 것이다
  - 컴파일 시에 컴파일러는 import문을 통해 소스파일에 사용된 클래스들의 패키지를 알아낸 다음, 모든 클래스이름 앞에 패키지명을 붙여 준다

```java
import 패키지명.클래스명;
또는
import 패키지명.*;
```

### static import문

- import문을 사용하면 클래스의 패키지명을 생략할 수 있는 것과 같이 static import문을 사용하면 static멤버를 호출할 때 클래스 이름을 생략할 수 있다
  - 특정 클래스의 static멤버를 자주 사용할 때 편리하며, 코드도 간결해진다

```java
import static java.lang.Math.*;

public class MathTest {
    public static void main(String[] args) {
        double result = sqrt(25.0);
        System.out.println("Square root: " + result);
    }
}
```

## 제어자(modifier)

### 제어자란?

- 제어자는 클래스, 변수 또느 메서드의 선언부에 함께 사용되어 부가적인 의미를 부여한다
- 제어자의 종류는 크게 접근 제어자와 그 외의 제어자로 나눌 수 있다
- 접근 제어자

| 접근 제어자 | 설명                                                                                     |
| ----------- | ---------------------------------------------------------------------------------------- |
| public      | 어떤 클래스에서든 접근이 가능합니다.                                                     |
| protected   | 같은 패키지 내에서는 접근이 가능하며, 다른 패키지의 자식 클래스에서도 접근이 가능합니다. |
| default     | 같은 패키지 내에서만 접근이 가능합니다.                                                  |
| private     | 해당 클래스 내에서만 접근이 가능하고, 외부 클래스에서는 접근이 불가능합니다.             |

- 그 외의 제어자

| 제어자       | 설명                                                                                              |
| ------------ | ------------------------------------------------------------------------------------------------- |
| static       | 클래스 멤버(변수 또는 메서드)로 선언하며, 객체 생성 없이 사용할 수 있습니다.                      |
| final        | 변수에 사용 시 값 변경이 불가능하며, 메서드에 사용 시 오버라이딩이 불가능합니다.                  |
| abstract     | 추상 클래스 또는 추상 메서드를 선언하는 데 사용되며, 구체적인 구현이 없는 추상 메서드를 가집니다. |
| transient    | 직렬화할 수 없는 필드를 표시하며, 객체의 상태를 파일에 저장할 때 사용됩니다.                      |
| volatile     | 멀티 스레딩 환경에서 변수의 값을 안전하게 읽고 쓸 수 있도록 합니다.                               |
| synchronized | 멀티 스레딩 환경에서 메서드 또는 블록을 동기화하여 스레드 간의 경쟁 상태를 방지합니다.            |
| strictfp     | 부동 소수점 연산의 표준을 정확히 따르도록 클래스 또는 메서드를 선언합니다.                        |
| native       | 자바 외부의 네이티브 코드(C, C++ 등)와 연결하여 사용하는 메서드를 선언합니다.                     |

- 제어자는 클래스나 멤버변수와 메서드에 주로 사용되며, 하나의 대상에 대해서 여러 제어자를 조합하여 사용하는 것이 가능하다
  - 단, 접근 제어자는 한 번에 네 가지 중 하나만 선택해서 사용할 수 있다
    - (제어자들 간의 순서는 관계없지만 주로 접근 제어자를 제일 왼쪽에 놓는 경향이 있다)

### static - 클래스의, 공통적인

- static은 '클래스의' 또는 '공통적인'의 의미를 가지고 있다
- 인스턴스 변수는 하나의 클래스로부터 생성되었더라도 각기 다른 값을 유지하지만, 클래스 변수는 인스턴스에 관계없이 같은 값을 갖는다
  - 하나의 변수를 모든 인스턴스가 공유하기 때문이다
- static이 붙은 멤버변수와 메서드, 그리고 초기화 블럭은 인스턴스가 아닌 클래스에 관계된 것이기 때문에 인스턴스를 생성하지 않고도 사용할 수 있다
- 인스턴스메서드와 static메서드의 근본적인 차이는 메서드 내에서 인스턴스 멤버를 사용하는 가의 여부에 있다

```java
static이 사용될 수 있는 곳 - 멤버변수, 메서드, 초기화 블럭
```

```java
public class MyClass {
  // 정적(static) 멤버 변수
  public static int staticVariable = 5;

  // 정적(static) 메서드
  public static void staticMethod() {
    System.out.println("이것은 정적 메서드입니다.");
  }

  public static void main(String[] args) {
    // 객체를 생성하지 않고 정적 멤버에 접근
    int value = MyClass.staticVariable;
    System.out.println("정적 멤버 변수의 값: " + value);

    MyClass.staticMethod(); // 정적 메서드 호출
  }
}
```

### final - 마지막의, 변경될 수 없는

- final은 '마지막의' 또는 '변경될 수 없는'의 의미를 가지고 있으며 거의 모든 대상에 사용될 수 있다
- 변수에 사용되면 값을 변경할 수 없는 상수가 되며, 메서드에 사용되면 오버라이딩을 할 수 없게 되고 클래스에 사용되면 자신을 확장하는 자손클래스를 정의하지 못하게 된다

```java
final이 사용될 수 있는 곳 - 클래스, 메서드, 멤버변수, 지역변수
```

```java
public class Example {
    // final 멤버 변수 (상수)
    final int finalMemberVariable = 10;

    // final 메서드
    final void finalMethod() {
        final int finalLocalVar = 20; // final 지역 변수 (상수)
        System.out.println("final 멤버 변수: " + finalMemberVariable);
        System.out.println("final 지역 변수: " + finalLocalVar);
    }

    // final 내부 클래스
    final class FinalInnerClass {
        void innerMethod() {
            System.out.println("final 내부 클래스의 메서드");
        }
    }

    public static void main(String[] args) {
        Example example = new Example();
        example.finalMethod();

        // final 내부 클래스의 인스턴스 생성
        FinalInnerClass finalInner = example.new FinalInnerClass();
        finalInner.innerMethod();
    }
}

```

### abstract - 추상의, 미완성의

- abstract는 '미완성'의 의미를 가지고 있다
- 메서드의 선언부만 작성하고 실제 수행내용은 구현하지 않은 추상 메서드를 선언하는데 사용된다

```java
abstract가 사용 될 수 있는 곳 - 클래스, 메서드
```

```java
public abstract class MyAbstractClass { // 추상 클래스
    abstract void myAbstractMethod(); // 추상 메서드
}
```

### 접근 제어자(access modifier)

- 접근 제어자는 멤버 또는 클래스에 사용되어 ,해당하는 멤버 또는 클래스를 외부에서 접근하지 못하도록 제한하는 역할을 한다

| 접근 제어자 | 접근 범위                                  |
| ----------- | ------------------------------------------ |
| public      | 모든 클래스에서 접근 가능                  |
| private     | 같은 클래스 내에서만 접근 가능             |
| protected   | 같은 패키지 또는 하위 클래스에서 접근 가능 |
| (default)   | 같은 패키지 내에서만 접근 가능             |

```java
public class MyClass {
    public int publicVar;    // 다른 클래스에서 접근 가능
    private int privateVar;  // 같은 클래스에서만 접근 가능
    protected int protectedVar;  // 같은 패키지 또는 하위 클래스에서 접근 가능
    int defaultVar;          // 같은 패키지에서만 접근 가능

    public void myMethod() {
        // 여기서는 모든 변수에 접근 가능
        publicVar = 10;
        privateVar = 20;
        protectedVar = 30;
        defaultVar = 40;
    }
}

class AnotherClass {
    public void anotherMethod() {
        MyClass myObject = new MyClass();
        myObject.publicVar = 100;    // public 변수에 접근 가능
        // myObject.privateVar = 200; // private 변수에 접근 불가능
        // myObject.protectedVar = 300; // protected 변수에 접근 불가능
        // myObject.defaultVar = 400;   // default 변수에 접근 불가능
    }
}
```

# 객체지향 프로그래밍

## 캡슐화와 접근 제어자

- 클래스나 멤버, 주로 멤버에 접근제어자를 사용하는 이유는 클래스의 내부에 선언된 데이터를 보호하기 위해서이다
  - 데이터가 유효한 값을 유지하도록, 또는 비밀번호와 같은 데이터를 외부에서 함부로 변경하지 못하도록 하기 위해서는 외부로부터의 접근을 제한하는 것이 필요하다
    - 이 것을 데이터 감추기(data hiding)라고 하며, 객체지향개념의 캡슐화(encapsulation)에 해당하는 내용이다
- 클래스 내에서만 사용되는, 내부 작업을 위해 임시로 사용되는 멤버변수나 부분작업을 처리하기 위한 메서드 등의 멤버들을 클래스 내부에 감추기 위해서이다
- 외부에서 접근할 필요가 없는 멤버들을 prinvate으로 지정하여 외부에 노출시키지 않음으로써 복잡성을 줄일 수 있다
  - 이 것 역시 캡슐화에 해당한다

```java
접근 제어자를 사용하는 이유
- 외부로부터 데이터를 보호하기 위해서
- 외부에는 불필요한, 내부적으로만 사용되는, 부분을 감추기 위해서
```

- 시간을 표시하기 위한 클래스 Time

```java
public class Time {
    public int hour;
    public int minute;
    public int second;
}
```

- 이 클래스의 인스턴스를 생성한 다음, 멤버변수에 직접 접근하여 값을 변경할 수 있을 것이다

```java
        Time t = new Time();
        t.hour = 25; // 멤버변수에 직접 접근
```

## 다형성

- 여러 가지 형태를 가질 수 있는 능력
  - 자바에서는 한 타입의 참조변수로 여러 타입의 객체를 참조할 수 있도록 함으로써 다형성을 프로그램적으로 구현하였다
    - 조상클래스 타입의 참조변수로 자손클래스의 인스턴스를 참조할 수 있도록 하였다는 것이다

**다형성의 핵심** 조상 타입의 참조변수를 사용하여 다양한 자손 클래스의 객체를 다룰 수 있습니다

```java
class Animal {
    void sound() {
        System.out.println("동물 소리를 내다.");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("개가 짖습니다.");
    }

    void fetch() {
        System.out.println("개가 물건을 가지고 옵니다.");
    }
}

class Cat extends Animal {
    @Override
    void sound() {
        System.out.println("고양이가 야옹 소리를 내다.");
    }
}

public class PolymorphismExample {
    public static void main(String[] args) {
        Animal myPet; // 조상 타입의 참조변수

        myPet = new Dog(); // Dog 객체를 Animal 참조변수로 참조
        myPet.sound(); // "개가 짖습니다." 출력

        myPet = new Cat(); // Cat 객체를 Animal 참조변수로 참조
        myPet.sound(); // "고양이가 야옹 소리를 내다." 출력

        // myPet.fetch(); // 에러! Animal 타입으로는 fetch 메서드에 접근 불가
    }
}

```

- myPet은 Animal 타입의 참조변수

  - 이 참조변수로 Dog 클래스와 Cat 클래스의 객체를 차례로 참조하고 있음
    - 이렇게 조상 타입의 참조변수를 사용하면, 다형성을 활용하여 다양한 객체를 관리할 수 있음

- myPet이 Dog 객체를 참조할 때 myPet.sound()를 호출하면 Dog 클래스의 sound 메서드가 실행됨
- myPet이 Cat 객체를 참조할 때 myPet.sound()를 호출하면 Cat 클래스의 sound 메서드가 실행됨
  - myPet은 Animal 타입으로 선언되었기 때문에 fetch 메서드에 접근할 수 없습니다.

```java
조상타입의 참조변수로 자손타입의 인스턴스를 참조할 수 있다
반대로 자손타입의 참조변수로 조상타입의 인스턴스를 참조할 수는 없다
```

### 참조변수의 형변화

- 기본형 변수와 같이 참조변수도 형변환이 가능하다
  - 단, 서로 상속관계에 있는 클래스 사이에서만 가능하다
    - 자손타입의 참조변수를 조상타입의 참조변수로, 조상타입의 참조변수를 자손타입의 참조변수로의 형변환만 가능하다
- 기본형 변수의 형변환에서 작은 자료형에서 큰 자료형의 형변환으 생략이 가능하듯이, 참조형 변수의 형변환에서는 자손타입의 참조변수를 조상타입으루 형변환하는 경우에는 형변환을 생략할 수 있다

```java
자손타입 -> 조상타입(Up-casting) : 형변환 생략가능
자손타입 <- 조상타입(Down-casting) : 형변환 생략불가
```

- 참조변수간의 형변환 역시 캐스트연산자를 사용하며, 괄호()안에 변환하고자 하는 타입의 이름(클래스명)을 적어주면된다

### instanceof 연산자

- 참조변수가 참조하고 있는 인스턴스의 실제 타입을 알아보기 위해 instanceof연산자를 사용한다
  - 주로 조건문에 사용되며, instanceof의 왼쪽에는 참조변수를 오른쪽에는 타입(클래스명)이 피연산자로 위치한다
    - 연산의 결과로 boolean값인 true와 false 중의 하나를 반환한다

```java
어떤 타입에 대한 instanceof연산의 결과가 true란느 것은 검사한 타입으로 형변환이 가능하다는 것을 뜻한다
```

```java
class Animal {
    void sound() {
        System.out.println("동물 소리를 내다.");
    }
}

class Dog extends Animal {
    @Override
    void sound() {
        System.out.println("개가 짖습니다.");
    }

    void fetch() {
        System.out.println("개가 물건을 가지고 옵니다.");
    }
}

public class TypeCastingExample {
    public static void main(String[] args) {
        Animal myPet = new Dog(); // Dog 객체를 Animal 참조변수로 참조

        myPet.sound(); // "개가 짖습니다." 출력

        if (myPet instanceof Dog) {
            Dog myDog = (Dog) myPet; // Dog 타입으로 형변환
            myDog.fetch(); // "개가 물건을 가지고 옵니다." 출력
        }
    }
}
```

- myPet이 Animal 타입의 참조변수로 선언되고 Dog 객체를 참조하고 있습니다
  - 다형성을 활용하여 sound() 메서드를 호출합니다
    - myPet이 실제로 Dog 객체를 참조하고 있는지 확인하기 위해 instanceof 연산자를 사용
      - 만약 myPet이 Dog 객체를 참조하고 있다면, Dog 타입으로 형변환하고 fetch() 메서드를 호출

### 참조변수와 인스턴스의 연결

- 참조변수가 어떤 클래스의 인스턴스를 가리키는지를 나타낸다
- 참조변수는 해당 클래스 또는 해당 클래스의 상위 클래스 또는 인터페이스의 인스턴스를 참조할 수 있습니다
  - 이것은 객체 지향 프로그래밍의 "하위 클래스는 상위 클래스의 형태를 띈다"라는 개념과 관련이 있습니다

```java
class Animal {
    void makeSound() {
        System.out.println("동물 소리를 내다.");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("멍멍!");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("야옹!");
    }
}

public class PolymorphismExample {
    public static void main(String[] args) {
        Animal myPet; // Animal 타입의 참조변수 선언

        myPet = new Dog(); // Dog 객체를 참조변수에 할당
        myPet.makeSound(); // "멍멍!" 출력

        myPet = new Cat(); // Cat 객체를 참조변수에 할당
        myPet.makeSound(); // "야옹!" 출력
    }
}

```

- myPet 참조변수가 new Dog()로 초기화된 경우 Dog 클래스의 인스턴스를 가리키고, new Cat()으로 초기화된 경우 Cat 클래스의 인스턴스를 가리킨다

### 매개변수의 다형성

- 메서드나 함수의 매개변수가 여러 다른 데이터 타입을 받을 수 있는 더 일반적인 형태의 매개변수를 가질 수 있음을 의미
  - 코드의 재사용성과 유연성이 증가하며, 다양한 데이터를 처리할 수 있게 됩니다

```java
1. 동일한 메서드나 함수를 여러 다른 데이터 타입에 대해 사용할 수 있습니다
2. 매개변수로 전달된 객체의 실제 타입에 따라 실행 시간에 해당 메서드나 함수가 다른 동작을 수행할 수 있습니다
3. 코드의 일반성과 재사용성을 높일 수 있습니다
```

- 매개변수의 다형성을 사용하여 `Animal` 타입의 매개변수를 받는 메서드를 만들면, 이 메서드는 `Animal` 타입 또는 그 하위 클래스인 `Dog` 또는 `Cat` 객체를 인수로 받을 수 있습니다
  - 메서드 내에서 해당 객체의 실제 타입을 확인하거나 다양한 작업을 수행할 수 있습니다

```java
class Animal {
    void makeSound() {
        System.out.println("동물 소리를 내다.");
    }
}

class Dog extends Animal {
    @Override
    void makeSound() {
        System.out.println("멍멍!");
    }
}

class Cat extends Animal {
    @Override
    void makeSound() {
        System.out.println("야옹!");
    }
}

public class PolymorphismExample {
    static void performSound(Animal animal) {
        animal.makeSound();
    }

    public static void main(String[] args) {
        Animal myPet = new Dog();
        performSound(myPet); // "멍멍!" 출력

        myPet = new Cat();
        performSound(myPet); // "야옹!" 출력
    }
}
```

- `performSound` 메서드는 `Animal` 타입의 매개변수를 받고 있습니다
  - `Dog`나 `Cat` 객체를 매개변수로 받아 각각의 소리를 출력할 수 있습니다
    - 동일한 메서드를 다양한 타입의 객체에 대해 사용할 수 있어 코드의 재사용성이 향상됩니다

### 여러 종류의 객체를 배열로 다루기

- 다형성(Polymorphism)을 이용하여 여러 클래스의 객체를 하나의 배열에 담아 관리하는 것을 의미한다
  - 조상타입의 참조변수로 자손타입의 객체를 참조하는 것이 가능

```java
class Animal {
    void sound() {
        System.out.println("동물 소리를 냅니다.");
    }
}

class Dog extends Animal {
    void sound() {
        System.out.println("멍멍!");
    }
}

class Cat extends Animal {
    void sound() {
        System.out.println("야옹!");
    }
}

public class Main {
    public static void main(String[] args) {
        // Animal 배열을 생성하고 다양한 동물 객체를 담습니다.
        Animal[] animals = new Animal[3];
        animals[0] = new Dog();
        animals[1] = new Cat();
        animals[2] = new Dog();

        // 배열을 반복하면서 각 동물의 소리를 출력합니다.
        for (Animal animal : animals) {
            animal.sound(); // 다형성을 활용하여 각 객체의 sound 메서드 호출
        }
    }
}

```

- Animal 클래스는 부모 클래스로서 Dog와 Cat 클래스가 상속받고 있습니다
  - 배열 animals는 Animal 타입으로 선언되었지만, 다형성 덕분에 Dog와 Cat 객체를 모두 담을 수 있습니다

## 추상클래스(abstract class)

### 추상클래스란?

- 미완성 클래스 / 완성되지 못한 채 남겨진 클래스
- 미완성이라는 것은 멤버의 개수에 관계된 것이 아니라, 단지 미완성 메서드(추상메서드)를 포함하고 있다는 의미이다
- 추상클래스로 인스턴스는 생성할 수 없다
  - 추상클래스는 상속을 통해서 자손클래스에 의해서만 완성될 수 있다
- 추상클래스 자체로는 클래스로서의 역할을 다 못 하지만, 새로운 클래스를 작성하는데 있어서 바탕이 되는 조상클래스로서 중요한 의미를 갖는다

```java
abstract class 클래스이름 {
    ...
}
```

- 추상클래스는 키워드 'abstract'를 붙이기만 하면된다
  - 이 클래스를 사용할 때, 클래스 선언부의 abstract를 보고 이 클래스에는 추상메서드가 있으니 상속을 통해서 구현해주어야 한다는 것을 알 수 있을 것이다
  - 추상클래스에도 생성자가 있으며, 멤버변수와 메서드도 가질 수 있다

### 추상메서드 (abstract method)

- 메서드는 선언부와 구현부로 구성되어 있다
  - 선언부만 작성하고 구현부는 작성하지 않은 채로 남겨 둔 것이 추상메서드이다
    - 즉, 설계만 해놓고 실제 수행될 내용은 작성하지 않았기 때문에 미완성 메서드인 것이다
- 메서드를 미완성 상태로 남겨 놓는 이유
  - 메서드의 내용이 상속받는 클래스에 따라 달라질 수 있기 때문에 조상 클래스에서는 선언부만ㅇ르 작성하고, 주석을 덧붙여 어떤 기능을 수행할 목적으로 작성되었는 지 알려 주고, 실제 내용은 상속받는 클래스에서 구현하도록 비워두는 것이다
    - 그래서 추상클래스를 상속받는 자손 클래스는 조상의 추상 메서드를 상황에 맞게 적절히 구현해주어야 한다

```java
// 주석을 통해 어떤 기능을 수행할 목적으로 작성하였는 지 설명한다
abstract 리턴타입 메서드이름();
```

- 키워드 abstract를 앞에 붙여 주고, 추상메서드는 구현부가 없으므로 괄호{}대신 문장의 끝을 알리는 ';'을 적어준다

```java
abstract class Player { // 추상클래스
    abstract  void play(int pos); // 추상메서드
    abstract  void stop(); // 추상메서드
}
class AudioPlayer extends Player {
    void play(int pos) { /* 내용생략 */ } // 추상메서드를 구현
    void stop() { /* 내용 생략 */ } // 추상메서드를 구현
}
abstract class AbstractPlayer extends Player {
    void play(int pos) { /* 내용 생략 */ } // 추상메서드를 구현
}
```

- 추상클래스로부터 상속받는 자손클래스는 오버라이딩을 통해 조상인 추상클래스의 추상메서드를 모두 구현해줘야한다
  - 조상으로부터 상속받은 추상메서드 중 하나라도 구현하지 않는다면, 자손클래스 역시 추상클래스로 지정해줘야한다

### 추상클래스의 작성

- 추상화는 기존의 클래스의 공통부분을 뽑아내서 조상 클래스를 만드는 것이라고 할 수 있다
- 추상화를 구체화와 반대되는 의미로 이해하면 보다 쉽게 이해할 수 있다
  - 상속계층도를 따라 내려갈수록 클래스는 점점 기능이 추가되어 구체화의 정도가 심해지며, 상속 계층도를 따라 올라갈수록 클래스는 추상화의 정도가 심해진다고 할 수 있다
    - 즉, 상속계층도를 따라 내려 갈수록 세분화되며, 올라갈수록 공통요소만 남게 된다

<img width="300" alt="image" src="https://github.com/nohheeyeon/TIL/assets/130336617/71bda9bb-7e1e-41e0-8815-f6774bfb61ee"> <br>

```java
// 추상 클래스 Animal
abstract class Animal {
    // 추상 메서드 speak 선언
    abstract void speak();
}

// 추상 클래스 Animal을 상속받은 구체 클래스 Dog
class Dog extends Animal {
    @Override
    void speak() {
        System.out.println("멍멍!");
    }
}

// 추상 클래스 Animal을 상속받은 구체 클래스 Cat
class Cat extends Animal {
    @Override
    void speak() {
        System.out.println("야옹!");
    }
}

public class AbstractClassExample {
    public static void main(String[] args) {
        Animal dog = new Dog();
        Animal cat = new Cat();

        dog.speak(); // "멍멍!" 출력
        cat.speak(); // "야옹!" 출력
    }
}
```

## 인터페이스(interface)

### 인터페이스란?

- 일종의 추상클래스다
- 인터페이스는 추상클래스처럼 추상메서드를 갖지만 추상클래스보다 추상화 정도가 높아서 추상클래스와 달리 몸통을 갖춘 일반 메서드 또는 멤버변수를 구성원으로 가질 수 없다
  - 오직 추상메서드와 상수만을 멤버로 가질 수 있으며, 그 외의 다른 어떠한 요소도 허용하지 않는다
- 인터페이스는 구현된 것은 아무 것도 없고 밑그림만 그려져 있는 '기본 설계도'라 할 수 있다
- 인터페이스도 추상클래스처럼 완성되지 않은 불완전한 것이기 때문에 그 자체만으로 사용되기 보다는 다른 클래스를 작성하는데 도움 줄 목적으로 작성된다

### 인터페이스의 작성

- 키워드로 interface를 사용
- interface에도 클래스와 같이 접근제어자로 public 또는 default를 사용할 수 있다

<!-- 왜 public과 default만 접근제어자로 사용 가능한 거지 -->

```java
interface 인터페이스이름 {
    public static rfinal 타입 상수이름 = 값;
    public abstract 메서드이름(매개변수목록);
}
```

- 일반적인 클래스의 멤버들과 달리 인터페이스의 멤버들이 가지고 있는 제약사항

```java
- 모든 멤버변수는 public static final 이어야 하며, 이를 생략할 수 있다
- 모든 메서드는 public abstract 이어야 하며,  이를 생략할 수 있다
```

-> 인터페이스에 정의된 모든 멤버에 예외없이 적용되는 사항이기 때문에 제어자를 생략할 수 있는 것이며, 편의상 생략하는 경우가 많다 <br>
-> 생략된 제어자는 컴파일 시에 컴파일러가 자동으로 추가해준다

### 인터페이스의 상속

- 인터페이스는 인터페이스로부터만 상속받을 수 있으며, 클래스와는 달리 다중상속, 즉 여러 개의 인터페이스로부터 상속을 받는 것이 가능하다
- 인터페이스는 클래스와 달리 Object클래스와 같은 최고 조상이 없다
<!-- 왜 -->

```java
interface Movable {
    /** 지정된 위치 (x, y)로 이동하는 기능의 메서드 */
    void move(int x, int y);
}
interface Attackable {
    /** 지정된 대상(u)을 공격하는 기능의 메서드 */
    void attact(Unit u);
}

interface Fightable extends Movable, Attackable { }
```

- 클래스의 상속과 마찬가지로 자손 인터페이스(Fightable)는 조상 인터페이스(Moveable, Attackable)에 정의된 멤버를 모두 상속받는다

### 인터페이스의 구현

- 인터페이스도 추상클래스처럼 그 자체로는 인스턴스를 생성할 수 없으며, 추상클래스가 상속을 통해 추상메서드를 완성하는 것처럼, 인터페이스도 자신에 정의된 추상메서드의 몸통을 만들어주는 클래스를 작성해야 하는데, 그 방법은 추상클래스가 자신을 상속받는 클래스를 정의하는 것과 다르지않다
  - But! ㅋ르래스는 확장한다는 의미의 키워드 'extends'를 사용하지만 인터페이스를 구현한다는 의미의 키워드 'implements'를 사용할 뿐이다

```java
class 클래스이름 implements 인터페이스이름 {
    // 인터페이스에 정의된 추상메서드를 구현해야 한다
}

class Fighter implements Fightable {
    public void move(int x, int y) { ... }
    public void attack(Unit u) { ... }
}
```

-> 'Fighter클래스는 Fightable인터페이스를 구현한다.'라고 한다

- 만일 구현하는 인터페이스의 메서드 중 일부만 구현한다면, abstract를 붙여서 추상클래스로 선언해야 한다

```java
abstract class Fighter implements Fightable {
    public void move(int x, int y) { ... }
}
```

- 상속과 구현을 동시에 할 수도 있다

```java
class Fighter extends Unit implements Fightable {
    public void move(int x, int y) { ... }
    public void attack(Unit u) { ... }
}
```

### 인터페이스를 이용한 다중상속

```java
// 인터페이스 Animal 정의
interface Animal {
    void makeSound();
}

// 강아지를 나타내는 Dog 클래스
class Dog implements Animal {
    @Override
    public void makeSound() {
        System.out.println("멍멍!");
    }
}

// 고양이를 나타내는 Cat 클래스
class Cat implements Animal {
    @Override
    public void makeSound() {
        System.out.println("냥냥!");
    }
}

public class AnimalExample {
    public static void main(String[] args) {
        Animal dog = new Dog();
        Animal cat = new Cat();

        dog.makeSound();  // "멍멍!" 출력
        cat.makeSound();  // "냥냥!" 출력
    }
}
```

- Animal 인터페이스를 구현한 Dog 클래스와 Cat 클래스가 각각 makeSound() 메서드를 구현하고 있다
  - 이 두 클래스는 인터페이스를 통해 다중 상속을 구현하고, main 메서드에서 Animal 인터페이스를 참조 변수로 사용하여 강아지와 고양이의 소리를 출력합니다

### 인터페이스를 이용한 다형성

### 인터페이스의 장점

```java
- 개발시간을 단축시킬 수 있다
- 표준화가 가능하다
-서로 관계없는 클래스들에게 관계를 맺어줄 수 있다
- 독립적인 프로그래밍이 가능하다
```

### 인터페이스의 이해

### 디폴트 메서드와 static메서드

- 자바를 보다 쉽게 배울 수 있도록 규칙을 단순히 할 필요가 있어서 인터페이스의 모든 메서드는 추상 메서드이어야 한다는 규칙에 예외를 두지 않았다
  - 인터페이스와 관련된 static메서드는 별도의 클래스에 따로 두어야 했다
- 가장 대표적인 것 : java.util.Collection인터페이스
  - 이 인터페이스와 관련도니 static메서드들이 인터페이스에는 추상 메서드만 선언할 수 있다는 원칙 때문에 별도의 클래스, Collections라는 클래스에 들어가게 되었다
  - 인터페이스 static메서드를 추가할 수 있었다면, Collections클래스는 존재하지 않았을 것이다
    - 인터페이스의 static메서드 역시 접근 제어자가 항상 public이며, 생략할 수 있다

#### 디폴트 메서드

- 새로 추가된 디폴트 메서드가 기존의 메서드와 이름이 중복되어 충돌하는 경우가 발생했을 때, 해결하는 규칙

```java
1. 여러 인터페이스의 디폴트 메서드 간의 충돌
    - 인터페이스를 구현한 클래스에서 디폴트 메서들르 오버라이딩해야 한다
2. 디폴트 메서드와 조상 클래스의 메서드 간의 충돌
     - 조상 클래스의 메서드가 상속되고, 디폴트 메서드는 무시된다
```

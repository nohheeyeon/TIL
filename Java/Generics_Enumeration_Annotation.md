# 지네릭스(Generics)

## 지네릭스란?

- 지네릭스는 다양한 타입의 객체들을 다루는 메서드나 컬렉션 클래스에 컴파일 시의 타입체크(compile-time type check)를 해주는 기능이다
  - 객체의 타입을 컴파일 시에 체크하기 때문에 객체의 타입 안정성을 높이고 형변환의 번거로움이 줄어든다
    - 타입 안정성을 높인다는 것은 의도하지 않은 타입의 객체가 저장되는 것을 막고, 저장된 객체를 꺼내올 때 원래의 타입과 다른 타입으로 잘못 형변환되어 발생할 수 있는 오류를 줄여준다는 뜻이다
- ex) ArrayList와 같은 컬렉션 클래스는 다양한 종류의 객체를 담을 수 있긴 하지만 보통 한 종류의 객체를 담는 겨우가 더 많다 <br>
  -> 그런데도 꺼낼 때 마다 타입체크를 하고 형변환을 하는 것은 아무래도 불편할 수 밖에 없다, 게다가 원하는 않는 종류의 객체가 포함되는 것을 막을 방법이 없다는 것도 문제다 <br>
  -> 지네릭스가 해결해준다

```java
지네릭스의 장점
1. 타입 안정성을 제공한다
2. 타입체크와 형변환을 생략할 수 있으므로 코드가 간결해진다
```

- 다룰 객체의 타입을 미리 명시해줌으로써 번거로운 형변환을 줄여준다

## 지네릭 클래스의 선언

- 지네릭 타입은 클래스와 메서드에 선언할 수 있다
- 클래스에 선언하는 지네릭 타입

```java
class Box {
    Object item;

    void setItem(Object item) { this.item = item; }
    Object getItem() { return item; }
}
```

- 클래스 Box

```java
class Box<T> { // 지네릭 타입 T를 선언
    T item;

    void setItem(T item) { this.item = item; }
    T getItem() { return item; }
}
```

- Box 클래스를 지네릭 클래스로 변경하면 클래스 옆에 <T>를 붙이면 된다

  - 그리고 Object를 모두 T로 바꾼다

- Box<T>에서 T를 '타입 변수(type variable'라고 하며, 'Type'의 첫 글자에서 따온 것이다
  - 타입 변수는 T가 아닌 다른 것을 사용해도 된다
- ArrayList<E>의 경우, 타입 변수 E는 'Element(요소)'의 첫 글자를 따서 사용했다
- 타입 변수가 여러 개인 경우에는 Map<K, V>와 같이 콤마 ','를 구분자로 나열함녀 된다

  - k는 Key(키)를 의미하고, V는 Value(값)을 의미한다 \* 무조건 'T'를 사용하기보다 가능하면, 상황에 맞게 의미있는 문자를 사용하는 것이 좋다 <br>
    **이들은 기호의 종류만 다를 뿐 '임의의 참조형 타입'을 의미한다는 것은 모두 같다**

- 지네릭 클래스가 된 Box클래스의 객체를 생성할 때는 참조변수와 생성자에 타입 T대신에 사용될 실제 타입을 지정해주어야 한다

```markdown
Box<String> b = new Box<String>(); // 타입 T 대신, 실제 타입을 지정
b.setItem(new Object()); // 에러! String이외의 타입은 지정불가
b.setItem("ABC"); // String 타입이므로 가능
String item = ~~(Stirng)~~ b.getItem(); // 형변환이 필요없음
```

- T 대신 String 타입을 지정해줌

```java
class Box { // 지네릭 타입을 String으로 지정
    String item;

    void setItem(String item) { this.item = item; }
    String getItem() { return item; }
}
```

- 지네릭 클래스 Box<T>는 위와 같이 정의된 것과 같다

### 지네릭스의 용어

```java
class Box<T> {}
```

```java
Box<T> : 지네릭 클래스. 'T의 Box' 또는 'T Box'라고 읽는다
T : 타입 변수 또는 타입 매개변수(T는 타입 문자)
Box : 원시 타입(raw type)
```

### 지네릭스의 제한

- 지네릭 클래스 Box의 객체를 생성할 때, 객체별로 다른 타입을 지정하는 것은 적절하다
  - 지네릭스는 인스턴스별로 다르게 동작하도록 하려고 만든 기능이니까!

```java
Box<Apple> appleBox = new Box<Apple>(); // Apple객체만 저장가능
Box<Grape> grapeBox = new Box<Grape>(); // Grape객체만 저장가능
```

- 모든 객체에 대해 동일하게 동작해야하는 static멤버에 타입 변수 T를 사용할 수 없다
  - T는 인스턴스 변수로 간주되기 때문이다
    - static멤버는 인스턴스변수를 참조할 수 없다

```java
class Box<T> {
    static T item; // 에러!
    static int compare(T t1, T t2) { ... } // 에러
        ...
}
```

### 지네릭 클래스의 객체 생성과 사용

- 지네릭 클래스를 사용하기 위해 객체를 생성

```java
Box<String> box = new Box<>();
```

### 제한된 지네릭 클래스

- 지네릭 타입을 특정한 범위의 클래스로 제한할 수 있습니다
  - 예를 들어, 특정 인터페이스를 구현한 클래스만 허용하는 경우

```java
class Box<T extends SomeInterface> {
    // ...
}
```

### 와일드 카드

- 와일드 카드(`?`)는 모든 지네릭 타입을 대신할 수 있는 특별한 타입입니다
  - 와일드 카드는 유연한 매개변수로 메서드를 작성할 때 사용됩니다

```java
public void printList(List<?> list) {
    for (Object o : list) {
        System.out.println(o);
    }
}
```

### 지네릭 메서드

- 지네릭 메서드는 메서드 내에서 사용되는 데이터 타입을 파라미터로 지정할 수 있는 메서드입니다

```java
public <T> T exampleMethod(T t) {
    // ...
    return t;
}
```

### 지네릭 타입의 형변환

- 지네릭 타입에서 다른 타입으로 형변환을 할 때, 원시 타입으로 형변환하는 것은 피해야 합니다
  - 대신, 와일드 카드나 instanceof 연산자를 사용하여 안전한 형변환을 진행해야 합니다

# 열거형 (Enums)

**열거형**은 명명된 상수의 집합을 나타내는 데이터 타입입니다

- 열거형은 주로 관련된 상수를 그룹화하고 명명하는 데 사용됩니다.

### 열거형이란?

```java
enum Day {
    SUNDAY, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY
}
```

### 열거형의 정의와 사용

```java
Day today = Day.MONDAY;
if (today == Day.MONDAY) {
    System.out.println("Today is Monday.");
}
```

### 열거형에 멤버 추가하기

- 열거형에 멤버를 추가할 수 있습니다
  - 각 멤버는 세미콜론(`;`)으로 끝나야 합니다

```java
enum Color {
    RED, GREEN, BLUE
}
```

# 애너테이션 (Annotations)

**애너테이션**은 메타데이터를 소스 코드에 추가하여 컴파일러와 다른 도구가 코드에 대한 정보를 처리하도록 지시합니다

## 애너테이션이란?

애너테이션은 다음과 같이 정의합니다:

```java
@interface MyAnnotation {
    String value() default "default value";
}
```

### 표준 애너테이션

- 자바에서는 다양한 표준 애너테이션을 제공합니다
  - `@Override`, `@Deprecated`, `@SuppressWarnings` 등이 있습니다

### 메타 애너테이션

- 메타 애너테이션은 다른 애너테이션을 위한 애너테이션으로, 커스텀 애너테이션을 정의할 때 사용됩니다

```java
@Retention(RetentionPolicy.RUNTIME)
@Target(ElementType.METHOD)
@interface MyCustomAnnotation {
    String value();
}
```

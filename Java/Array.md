## 배열(Array)

### 배열이란?

- 배열은 동일한 데이터 유형을 가진 여러 값을 저장하는 자료 구조
- `int` 타입의 배열은 정수 값을 저장하는 데 사용됨
- 각 값은 배열 내에서 고유한 위치인 인덱스를 가짐

### 배열의 선언과 생성

- 배열을 선언하려면 해당 데이터 유형을 지정하고 배열 변수의 이름을 지정
- 그런 다음 `new` 연산자를 사용하여 배열을 생성하고 크기를 지정

```java
int[] numbers = new int[5]; // 크기가 5인 int 배열 생성
```

### 배열의 길이와 인덱스

- 배열의 길이는 배열에 저장된 요소의 개수를 나타냅니다
- 배열의 인덱스는 0부터 시작하며, 배열 길이보다 작은 값을 가질 수 있습니다
  - ex) 길이가 5인 배열의 인덱스는 0부터 4까지입니다.

### 배열의 초기화

- 배열을 초기화하려면 배열의 각 요소에 값을 할당해야 합니다
- 초기화는 배열 선언과 동시에 수행할 수 있으며, 나중에 개별적으로 수행할 수도 있습니다

```java
int[] numbers = {1, 2, 3, 4, 5}; // 배열 선언 및 초기화
```

### 배열의 복사

- `System.arraycopy()` 메서드를 사용하거나, 새로운 배열을 만들어 값을 복사할 수 있습니다

```java
int[] source = {1, 2, 3};
int[] target = new int[source.length];
System.arraycopy(source, 0, target, 0, source.length); // 배열 복사
```

### 배열의 활용

- 배열은 데이터를 저장, 검색, 정렬 및 필터링하는 데 사용됩니다
- 배열은 다른 자료 구조를 구현하는 데 기반이 되는 중요한 개념입니다

## String 배열

### String 배열의 선언과 생성

- `String` 배열은 문자열을 저장하는 데 사용됩니다
- 선언 및 생성 방법은 기본 데이터 유형 배열과 유사합니다

```java
String[] names = new String[3]; // 크기가 3인 String 배열 생성
```

### String 배열의 초기화

- `String` 배열을 초기화하려면 각 요소에 문자열을 할당하면 됩니다

```java
String[] names = {"Alice", "Bob", "Charlie"}; // 배열 선언 및 초기화
```

### char 배열과 String 클래스

- `char` 배열은 문자의 배열로, 문자열을 처리하는 데 사용됩니다
- `String` 클래스는 문자열을 다루는 다양한 메서드와 함께 제공되며, 문자열 처리에 편리하게 사용됩니다

```java
char[] charArray = {'H', 'e', 'l', 'l', 'o'};
String str = new String(charArray); // char 배열을 String으로 변환
```

### 커맨드 라인을 통해 입력받기

- 커맨드 라인에서 사용자 입력을 받아와 `String` 배열에 저장하는 방법을 이용하여 프로그램을 작성할 수 있습니다

```java
public class CommandLineInput {
    public static void main(String[] args) {
        for (String arg : args) {
            System.out.println(arg);
        }
    }
}
```

## 다차원 배열

### 2차원 배열의 선언과 인덱스

- 2차원 배열은 행과 열로 구성되며, 각 요소는 두 개의 인덱스를 사용하여 접근됩니다

```java
int[][] matrix = new int[3][4]; // 3x4 크기의 2차원 배열 생성
```

### 2차원 배열의 초기화

- 2차원 배열을 초기화하려면 각 요소에 값을 할당하면 됩니다
- 중첩된 `for` 루프를 사용하여 초기화할 수 있습니다

```java
int[][] matrix

 = {{1, 2, 3}, {4, 5, 6}, {7, 8, 9}}; // 2차원 배열 초기화
```

### 가변 배열

- 가변 배열은 각 행의 길이가 서로 다른 배열입니다
  -> 이를 통해 다양한 데이터 구조를 모델링할 수 있습니다

```java
int[][] jaggedArray = new int[3][];
jaggedArray[0] = new int[]{1, 2};
jaggedArray[1] = new int[]{3, 4, 5};
jaggedArray[2] = new int[]{6};
```

### 다차원 배열의 활용

- 다차원 배열은 행렬, 이미지, 게임 보드 등 다양한 응용 프로그램에서 사용됩니다

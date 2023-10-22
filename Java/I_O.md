# 자바에서의 입출력

## 입출력이란?

- I/O란 Input과 Output의 약자로 입력과 출력, 간단히 줄여서 입출력이라고 한다
  - 입출력은 컴퓨터 내부 또는 외부의 장치와 프로그램간의 데이터를 주고받는 것을 말한다

## 스트림(stream)

- 자바에서 입출력을 수행하려면, 즉 어느 한쪽에서 다른 쪽으로 데이터를 전달하려면, 두 대상을 연결하고 데이터를 전송할 수 있는 무언가가 필요한데 이것을 스트림(stream)이라고 정의했다

```java
스트림이란 데이터를 운반하는데 사용되는 연결통로이다
```

- 스트림은 단방향통신과 가능하기 때무에 하나의 스트림으로 입력과출력을 동시에 처리할 수 없다
  - 그래서 입력과 출력을 동시에 수행하려면 입력을 위한 입력스트림(input stream)과 출력을 위한 출력스트림(output stream), 모두 2개의 스트림이 필요하다 <br>
    <img width="337" alt="image" src="https://github.com/nohheeyeon/nohheeyeon/assets/130336617/52ec6ce5-fafb-4d91-a665-6f88c778a2a0">
    <br>
- 스트림은 먼저 보낸 데이터를 먼저 받게 되어 있으며 중간에 건너뜀 없이 연속적으로 데이터를 주고받는다

## 바이트기반 스트림 - InputStream, OutputStream

- 스트림은 바이트단위로 데이터를 전송하며 입출력 대상에 따라 입출력스트림이 있다

  | 대상 종류               | 입력 스트림          | 출력 스트림           |
  | ----------------------- | -------------------- | --------------------- |
  | 바이트 기반 기본 클래스 | InputStream          | OutputStream          |
  | 파일                    | FileInputStream      | FileOutputStream      |
  | 바이트 배열             | ByteArrayInputStream | ByteArrayOutputStream |
  | 파이프                  | PipedInputStream     | PipedOutputStream     |
  | 객체                    | ObjectInputStream    | ObjectOutputStream    |
  | 문자 변환               | InputStreamReader    | OutputStreamWriter    |
  | 문자 기반 파일          | FileReader           | FileWriter            |
  | 네트워크 (소켓)         | SocketInputStream    | SocketOutputStream    |
  | 버퍼링                  | BufferedInputStream  | BufferedOutputStream  |

- 어떠한 대상에 대해서 작업을 할 것인 지 그리고 입력을 할 것인 지 출력을 할 것 인 지에 따라서 스트림을 선택해서 사용하면 된다
  - ex) 어떤 파일의 내용을 읽고자 하는 경우에는 FileInputStream을 사용하면 됨!
- 이들은 모두 InputStream 또는 OutStream의 자손들이며, 각각 읽고 쓰는데 필요한 추상메서드를 자신에 맞게 구현해놓았다

## 보조스트림

- 스트림의 기능을 보완하기 위해!
  - 보조스트림은 실제 데이터를 주고받는 스트림이 아니기 때문에 데이터를 입출력할 수 있는 기능은 없지만, 스트림의 기능을 향상시키거나 새로운 기능을 추가할 수 있다
    - 그래서 보조스트림만으로는 입출력을 처리할 수 없고, 스트림을 먼저 생성한 다음에 이를 이용해서 보조스트림을 생성해야한다
- ex) test.txt라는 파일을 읽기위해 FileInputStream을 사용할 때, 입력 성능을 향상시키기 위해 버퍼를 사용하는 보조스트림인 BufferedInputStream을 사용하는 코드!

```java
// 먼저 기반스트림을 생성한다
FileInputStream fis = new FileInputStream("test.txt");

// 기반스트림을 이용해서 보조스트림을 생성한다
BufferedInputStream bis = new BufferedInputStream(fis);

bis.read(); // 보조스트림인 BufferedInputStream으로부터 데이터를 읽는다
```

- 코드 상으로는 보조스트림인 BufferedInputStream이 입력기능을 수행하는 것처럼 보이지만, 실제 입력기능은 BufferedInputStream과 연결된 FileInputStream이 수행하고, 보조스트림인 BufferedInputStream은 버퍼만을 제공한다
  - 버퍼를 사용한 입출력과 사용하지 않은 입출력간의 성능차이는 상당하기 때문에 대부분의 경우에 버퍼를 이용한 보조스트림을 사용한다

| 입력 보조 스트림    | 출력 보조 스트림     | 설명                                                                       |
| ------------------- | -------------------- | -------------------------------------------------------------------------- |
| BufferedInputStream | BufferedOutputStream | 기본 스트림에 버퍼링 기능을 추가한다.                                      |
| BufferedReader      | BufferedWriter       | 문자 기반 스트림에 버퍼링 기능을 추가한다.                                 |
| InputStreamReader   | OutputStreamWriter   | 바이트 기반 스트림과 문자 기반 스트림 간의 변환을 제공한다.                |
| DataInputStream     | DataOutputStream     | 기본 데이터 타입(primitive data type)을 입출력한다.                        |
| ObjectInputStream   | ObjectOutputStream   | 객체를 입력/출력하기 위해 사용한다. 객체 직렬화에 필요하다.                |
| PushbackInputStream | (없음)               | 바이트나 배열을 스트림에 다시 푸시하여 다시 읽을 수 있게 한다.             |
| SequenceInputStream | (없음)               | 두 개의 입력 스트림을 연속적으로 연결한다.                                 |
| PrintStream         | (출력만 해당)        | 바이트 출력 스트림으로 텍스트 데이터를 출력한다. 예로 `System.out`이 있다. |

## 문자기반 스트림 - Reader, Writer

- C언어와 달리 Java에서는 한 문자를 의미하는 char형이 1 byte가 아니라 2 byte이기 때문에 바이트기반의 스트림으로 2 byte인 문자를 처리하는 데는 어려움이 있다
  - 이 점을 보완하기 위해서 문자기반의 스트림이 제공된다
    - 문자데이터를 입출력할 때는 바이트기반 스트림 대신 문자기반 스트림을 사용하자!

```java
InputStream -> Reader
OutputStream -> Writer
```

| 바이트기반 스트림    | 문자기반 스트림 |
| -------------------- | --------------- |
| FileInputStream      | FileReader      |
| FileOutputStream     | FileWriter      |
| BufferedInputStream  | BufferedReader  |
| BufferedOutputStream | BufferedWriter  |

- [바이트기반 스트림과 문자기반 스트림의 비교]

| 기능 | 바이트기반 스트림 메서드 | 문자기반 스트림 메서드 |
| ---- | ------------------------ | ---------------------- |
| 읽기 | read()                   | read()                 |
| 쓰기 | write(byte[])            | write(char[])          |
| 닫기 | close()                  | close()                |

- [바이트기반 스트림과 문자기반 스트림의 읽고 쓰는 메서드 비교]

| 바이트 기반 보조 스트림 | 문자 기반 보조 스트림 |
| ----------------------- | --------------------- |
| BufferedInputStream     | BufferedReader        |
| BufferedOutputStream    | BufferedWriter        |
| DataInputStream         | -                     |
| DataOutputStream        | -                     |
| ObjectInputStream       | -                     |
| ObjectOutputStream      | -                     |
| PushbackInputStream     | PushbackReader        |
| SequenceInputStream     | -                     |
| PrintStream             | PrintWriter           |
| InputStream             | InputStreamReader     |
| OutputStream            | OutputStreamWriter    |

- [바이트기반 보조스트림과 문자기반 보조스트림]

# 바이트기반 스트림

## InputStream과 OutputStream

- InputStream과 OutputStream은 모든 바이트기반의 스트림의 조상이다

  | 메서드명                             | 설명                                                      |
  | ------------------------------------ | --------------------------------------------------------- |
  | int read()                           | 입력 스트림으로부터 한 바이트를 읽어들입니다.             |
  | int read(byte[] b)                   | 주어진 바이트 배열에 데이터를 읽어들입니다.               |
  | int read(byte[] b, int off, int len) | 주어진 바이트 배열의 특정 영역에 데이터를 읽어들입니다.   |
  | long skip(long n)                    | 주어진 수만큼의 바이트를 건너뜁니다.                      |
  | int available()                      | 읽을 수 있는 남아있는 바이트의 추정량을 반환합니다.       |
  | void close()                         | 입력 스트림을 닫고 관련된 시스템 자원을 해제합니다.       |
  | void mark(int readlimit)             | 현재 위치를 표시합니다.                                   |
  | void reset()                         | 스트림을 마지막으로 표시된 위치로 되돌립니다.             |
  | boolean markSupported()              | 스트림이 mark()와 reset() 메서드를 지원하는지 확인합니다. |

- [InputStream의 메서드]

| 메서드명                               | 설명                                                     |
| -------------------------------------- | -------------------------------------------------------- |
| void write(int b)                      | 한 바이트를 출력 스트림에 씁니다.                        |
| void write(byte[] b)                   | 주어진 바이트 배열의 모든 바이트를 출력 스트림에 씁니다. |
| void write(byte[] b, int off, int len) | 바이트 배열의 특정 영역을 출력 스트림에 씁니다.          |
| void flush()                           | 버퍼링된 모든 출력 바이트를 강제로 내보냅니다.           |
| void close()                           | 출력 스트림을 닫고 관련된 시스템 자원을 해제합니다.      |

- [OutputStream의 메서드]

- 스트림의 종류에 따라서 mark()와 reset()을 사용하여 이미 읽은 데이터를 되돌려서 다시 읽을 수 있다
  - 이 기능을 지원하면 스트림인지 확인하는 markSuppoprted()를 통해서 알 수 있다
- flush는 버퍼가 있는 출력스트림의 경우에만 의미가 있으며, OutputStream에 정의된 flush()는 아무런 일도 하지않는다
- 프로그램이 종료될 때, 사용하고 닫지 않은 스트림을 JVM이 자동적으로 닫아 주기는 하지만, 스트림을 사용해서 모든 작업을 마치고 난 후에는 close()를 호출해서 반드시 닫아주어야 한다
  - 그러나 ByteArrayInputStream과 같이 메모리를 사용하는 스트림과 System.in, System.out과 같은 표준 입출력 스트림은 닫아주지 않아도 된다

## ByteArrayInputStream/ByteArrayOutputStream

- 메모리의 바이트 배열을 소스 또는 대상으로 데이터를 읽거나 쓸 때 사용됩니다.
  - 파일이나 네트워크 대신 바이트 배열에서 데이터를 처리할 때 사용합니다
    ```java
    byte[] inputBytes = {0, 1, 2, 3, 4, 5};
    ByteArrayInputStream bais = new ByteArrayInputStream(inputBytes);
    ByteArrayOutputStream baos = new ByteArrayOutputStream();
    int data;
    while ((data = bais.read()) != -1) {
        baos.write(data);
    }
    byte[] outputBytes = baos.toByteArray();
    ```

## BufferedInputStream/BufferedOutputStream

- 내부 버퍼를 사용하여 입출력의 성능을 향상시키는 스트림입니다
  ```java
  try (BufferedInputStream bis = new BufferedInputStream(new FileInputStream("source.txt"));
       BufferedOutputStream bos = new BufferedOutputStream(new FileOutputStream("destination.txt"))) {
      int data;
      while ((data = bis.read()) != -1) {
          bos.write(data);
      }
  } catch (IOException e) {
      e.printStackTrace();
  }
  ```

## DataInputStream/DataOutputStream

- 기본 데이터 타입의 값 (예: int, double, boolean)을 바이트 스트림에 읽거나 쓰기 위해 사용됩니다
  ```java
  try (DataOutputStream dos = new DataOutputStream(new FileOutputStream("data.bin"))) {
      dos.writeInt(123);
      dos.writeDouble(123.456);
      dos.writeBoolean(true);
  } catch (IOException e) {
      e.printStackTrace();
  }
  ```

## SequenceInputStream

- 두 개의 입력 스트림을 연결하여 하나의 입력 스트림처럼 동작하게 합니다
  ```java
  try (FileInputStream fis1 = new FileInputStream("file1.txt");
       FileInputStream fis2 = new FileInputStream("file2.txt");
       SequenceInputStream sis = new SequenceInputStream(fis1, fis2);
       FileOutputStream fos = new FileOutputStream("combined.txt")) {
      int data;
      while ((data = sis.read()) != -1) {
          fos.write(data);
      }
  } catch (IOException e) {
      e.printStackTrace();
  }
  ```

## PrintStream

- 다양한 데이터 타입의 값을 출력할 수 있는 스트림입니다

  - 주로 `System.out` 객체로 사용됩니다

  ```java
  try (PrintStream ps = new PrintStream("output.txt")) {
      ps.println("Hello, World!");
      ps.println(12345);
      ps.println(true);
  } catch (IOException e) {
      e.printStackTrace();
  }
  ```

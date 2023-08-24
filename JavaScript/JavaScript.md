# JavaScript(ES6)

# 변수

```javascript
name = "Mike";
age = 30;
```

- ; : 한 줄이 끝났다는 의미
- "" : String

Javascript 예약어 주의

- alert()
- console.log()

-> 변수 명이 겹친다면 마지막에 기재된 변수가 실행된

- let
  -> 중복 시 오류 메세지
  -> 사용하고싶다면 let을 넣으면 됨
- const
  -> 절대로 바뀌지 않는 상수
  -> 수정 X(에러 발생함)
  -> 대문자를 쓰는 게 좋음

### 자바스크립트에서 변수를 선언할 때

- 변하지 않는 값은 const
- 변할 수 있는 값은 let으로 선언

## 변수 주의

- 변수는 문자와 숫자, $와 \_만 사용
- 첫글자는 숫자가 될 수 없다
- 예약어를 사용할 수 없다
- 가급적 상수는 대문자로
- 변수명은 읽기 쉽고 이해할 수 있게 선언

## 자료형

##### 문자형

```javascript
const name = "Mike"; // 문자형 String
const age = 30;

const name1 = "Mike";
const name2 = "Mike";
const name3 = `Mike`;

const message = "I'm a boy.";
const message2 = "I'm a boy.";

const message3 = `My name is ${name}`;

const message4 = `나는 ${30 + 1}살 입니다.`;
console.log(message);
```

##### 숫자형

```javascript
const age = 30; // 숫자형 Number
const PI - 3.14;

console.log(1 + 2); // 더하기
console.log(10 - 3); // 빼기
console.log(3 * 2); // 곱하기
console.log(6 / 3); // 나누기
console.log(6 % 4); // 나머지

const x = 1/10; // Infinity
console.log(x)

const name = "Mike";
const y = name/2;

console.log(y) // NaN

// NaN = Not a number

// Boolean

const a = true; // 참
const b = false; // 거짓

console name = "Mike";
const age = 30;

console.log(name == 'Mike)
console.log(age > 40)

// null 과 undefined

let user = null; // user는 존재하지않는다는 뜻

//객체형
//심볼형

// typeof 연산자

const name = "Mike";

console.log(typeof 3);
console.log(typeof name);
console.log(typeof ture);
console.log(typeof "xxx");
console.log(typeof null);
console.log(typeof undefined); // undefined

null
```

##### 대화상자

- alert : 알려줌
- prompt : 입력 받음
- confirm : 확인 받음

```javascript
const name = prompt("이름을 입력하세요.");
alert("환영합니다, " + name + "님");

const name = prompt("예약일을 입력해주세요.", "2020-10-");

const isAdult = confirm("당신은 성인입니까?"); // 확인 =  true, 취소 = false
console.log(isAdult);
```

단점

- 스크립트 일시 정지
- 스타일링 X

##### 형변환 ( Type Conversion )

- String() -> 문자형으로 변환
- Number() -> 숫자형으로 변환
  - Number("문자") -> NaN
- Boolean() -> 불린형으로 변환
  - 0, ", null, undefined, NaN -> false

```javascript
// 자동 형변환
"6" / "2" = 3
```

```javascript
console.log(
    String(3),
    String(true),
    String(false),
    String(null),
    String(undefined);
)

console.log(
    Number("1234"), // 1234
    Number("1234ASDF"), // NaN

    Number(true), // 1
    Number(false) // 0
);
```

Boolean

- false
  - 숫자 0
  - 빈 문자열 /"
  - null
  - undefined
  - NaN
    을 제외하고 모두 true

```javascript
// true
console.log(Boolean(1), Boolean(123), Boolean("javascript"));

// false
console.log(
  Boolean(0),
  Boolean(""),
  Boolean(null),
  Boolean(undefined),
  Boolean(NaN)
);
```

주의사항

```javascript
Number(null) // 0
Number(undefined) // NaN

Boolean(0) // false
Boolean('0') // true

Boolean(") // false
Boolean(' ') // true
```

##### 연산자(Operators)

```javascript
+ // 더하기
- // 빼기
* // 곱하기
/ // 나누기
% // 나머지
```

나머지(%)를 어디에 쓸까?

- 홀수 : X % 2 = 1
- 짝수 : Y % 2 = 0
- X % 5 = 0 ~ 4 사이의 값만 반환

- 거듭제곱
  const num = 2\*\*3;
  console.log(num); // 8
- 우선 순위
  - \*/ > +-
- 연산자 줄여서 쓰기

```javascript
let num = 18;
num = num + 5;
num += 5;

console.log(num);
```

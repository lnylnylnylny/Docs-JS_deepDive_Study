## 변수(Variable)

하나의 메모리 공간 그 자체, 식별자를 대신해서 칭하기도함, 값의 위치를 가르키는 상징적인 이름

```js
let userId = 1;
let userName = "Lee";
```

객체나 배열 같은 자료구조를 사용하면 여러 개의 값을 하나로 그룹화해서 하나의 값처럼 사용할 수 있다.

```js
const user = { id: 1, name: "Lee" };

const users = [
  { id: 1, name: "Lee" },
  { id: 2, name: "Kim" },
];
```

```js
let result = 10 + 20; // 식을 저장 = 30을 저장
let score; // 선언, 자동으로 undefined 할당
score = 30; // 할당 (할당 연산자)
```

```js
console.log(score); // undefined

let score; // 변수 선언
score = 80; // 값의 할당
===
let score = 80;

console.log(score); // 80
```

<br />

## 식별자(identifier)

식별자는 어떤 값을 구별해서 식별할 수 있는 고유한 이름을 말한다.
식별자는 값이 아니라 메모리 주소를 기억하고 있다.
즉, 식별자는 메모리 주소에 붙인 이름이라고 할 수 있다.

```js
// 식별자 - 메모리 주소 - 메모리
result -> 0X669F913 -> 30
```

<br />

## 선언(declaration)

변수, 함수, 클래스 등의 이름과 같은 식별자는 네이밍 규칙을 준수해야 하며, `선언` 에 의해 JS Engine에 식별자의 존재를 알린다.

변수 선언(variable declaration)이란, 변수를 생성하는 것을 말한다.
값을 저장하기 위한 메모리 공간을 확보하고 변수 이름과 확보된 메모리 공간의 주소를 연결해서 값을 저장할 수 있게 준비한다.

변수를 사용하려면 반드시 선언이 필요하다.
변수를 선언할 때는 var, let, const 키워드를 사용한다.

변수 선언은 선언 단계와 초기화 단계가 동시에 진행된다.

```js
var score; // 선언과 동시에 초기화, 즉 undefined를 할당해 초기화한다.
// 초기화를 하지 않으면 garbage value가 남기 때문에 값을 제대로 할당하지 못할 위험성이 있다.
```

<br />

## 호이스팅(hoisting)

변수 선언문이 코드의 선두로 끌어 올려진 것처럼 동작하는 자바스크립트 고유의 특징

모든 선언문은 런타임 이전 단계에서 먼저 실행된다.
변수의 할당은 런타임에 실행된다.

```js
console.log(score); //

score = 80; //
let score; //

console.log(score); //

=>

let score; //
console.log(score); //

score = 80; //

console.log(score); //
```

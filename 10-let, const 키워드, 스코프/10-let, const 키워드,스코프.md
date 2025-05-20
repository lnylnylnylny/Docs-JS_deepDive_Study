## [JavaScript] 원시 값과 객체의 비교

### JavaScript의 let, const와 블록 레벨 스코프 정리

자바스크립트를 학습하면서 반드시 이해해야 할 개념 중 하나는 스코프(scope)입니다. 스코프는 변수, 함수, 클래스 등 식별자가 어디서부터 어디까지 유효한지를 결정하는 기본이자 핵심 개념입니다. ES6에서 등장한 `let`과 `const`는 기존의 `var`와 다른 **블록 레벨 스코프**를 제공합니다. 이 포스트에서는 그 개념들을 총정리합니다.

---

### 스코프(Scope)란?

- 스코프는 **식별자가 유효한 범위**, 즉 해당 식별자를 참조할 수 있는 코드의 영역을 의미합니다.
- 모든 식별자는 **선언된 위치에 따라 유효 범위가 결정**됩니다.
- 자바스크립트의 스코프는 크게 전역 스코프(Global Scope)와 지역 스코프(Local Scope)로 나눌 수 있습니다.

| 구분   | 설명               | 스코프        | 변수 종류   |
|--------|--------------------|---------------|-------------|
| 전역   | 코드의 가장 바깥 영역 | 전역 스코프     | 전역 변수     |
| 지역   | 함수 내부            | 지역(함수) 스코프 | 지역 변수     |


---

### 함수 레벨 스코프 vs 블록 레벨 스코프

- **함수 레벨 스코프**: 오직 함수 몸체 내에서만 지역 스코프를 형성합니다. (`var`)
- **블록 레벨 스코프**: 모든 코드 블록(`{}`)이 지역 스코프를 생성합니다. (`let`, `const`)

```javascript
if (true) {
  var x = 1;
}
console.log(x); // 함수 레벨 스코프

if (true) {
  let y = 2;
}
console.log(y); // ReferenceError - 블록 레벨 스코프

```

---
### 블록 레벨 스코프 (Block-level Scope)
- 블록 레벨 스코프란 {} 중괄호로 감싼 블록 내부에서만 변수나 상수가 유효한 범위를 갖는 것을 말합니다.

- let과 const는 블록 레벨 스코프를 따르며, 이는 var와의 중요한 차이점입니다.

```js
if (true) {
  var a = 1;
  let b = 2;
  const c = 3;
}
console.log(a); //  1
console.log(b); // ReferenceError
console.log(c); // ReferenceError
```
| 키워드     | 스코프 종류    | 블록 내 유효성 | 재할당 가능 | TDZ(일시적 사각지대)      |
| ------- | --------- | -------- | ------ | ------------------ |
| `var`   | 함수 레벨 스코프 | X        | O      |  (undefined 반환)   |
| `let`   | 블록 레벨 스코프 | O        | O      |  (ReferenceError) |
| `const` | 블록 레벨 스코프 | O        | X      |  (ReferenceError) |

---

### let 키워드
- 블록 레벨 스코프를 갖습니다.

- 재할당이 가능합니다.

- 선언 전에 접근하면 ReferenceError가 발생합니다 (TDZ 존재).
```js
let count = 1;
count = 2;

if (true) {
  let msg = 'hello';
  console.log(msg); // hello
}
console.log(msg); // ReferenceError
```
---
### const 키워드
- 블록 레벨 스코프를 갖습니다.

- 재할당이 불가능합니다.

- 선언과 동시에 초기화해야 합니다.

- 객체/배열은 내부 프로퍼티 변경은 가능함.
``` js
const PI = 3.14;
PI = 3.1415; // TypeError

const user = { name: 'Alice' };
user.name = 'Bob'; // 가능
```

---
### 스코프 체인(Scope Chain)
- 스코프는 함수의 중첩에 따라 계층적으로 구성됩니다.

- 변수를 참조할 때, 자바스크립트 엔진은 현재 스코프에서 상위 스코프로 올라가며 선언된 식별자를 검색합니다.

``` js
const x = 1;

function outer() {
  const y = 2;
  function inner() {
    const z = 3;
    console.log(x, y, z); // 1 2 3
  }
  inner();
}
outer();
```
---
### 렉시컬 스코프(Lexical Scope)
- 자바스크립트는 렉시컬 스코프(정적 스코프)를 따릅니다.

- 함수를 정의한 위치에 따라 상위 스코프가 결정됩니다.

- 함수가 호출된 위치는 상위 스코프 결정에 영향을 주지 않습니다.

```js
const a = 'global';

function outer() {
  const a = 'outer';
  function inner() {
    console.log(a);
  }
  return inner;
}

const myFunc = outer();
myFunc(); // outer

```
--- 
### 호이스팅과 TDZ(Temporal Dead Zone)

| 키워드   | 호이스팅 | TDZ 발생 | 선언 전 접근 시      |
| ----- | ---- | ------ | -------------- |
| var   | O    | X      | undefined      |
| let   | O    | O      | ReferenceError |
| const | O    | O      | ReferenceError |

```js
console.log(a); // undefined
var a = 1;

console.log(b); // ReferenceError
let b = 2;
```

let과 const는 선언 전에 접근할 수 없는 일시적 사각지대(TDZ)에 들어가므로, 보다 안전한 코드를 작성할 수 있도록 도와줍니다.

---
 
 ### 마무리 요약
- let과 const는 블록 레벨 스코프를 지원해 코드 안정성과 가독성을 높입니다.

- 기본적으로는 const를 사용하고, 재할당이 필요한 경우에만 let을 사용합니다.

- var는 함수 레벨 스코프만 제공하며 예측하기 어려운 버그의 원인이 되므로 지양하는 것이 좋습니다.

- 스코프, 스코프 체인, 렉시컬 스코프는 변수 선언과 검색, 클로저 이해를 위한 필수 개념입니다.

- 스코프  => 자바스크립트 엔진이 식별자를 검색할 때 사용하는 규칙임

- 렉시컬 환경이란 코드가 어디서 실행되며 주변에 어떤 코드가 있는지 확인하는 환경

- 지역 변수 = 자신의 지역 스코프와 하위 지역 스코프에서 유효하다.


#### 전에 내용도 복습하며 학습을 진행하였음
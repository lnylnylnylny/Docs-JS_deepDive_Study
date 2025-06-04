# [28장 Number]

---

## 1. Number 생성자 함수

```js
const num1 = new Number(10);
console.log(num1); // Number { [[PrimitiveValue]]: 10 }

// 문자열 타입 -> 숫자 타입
Number("0");
Number("-1");

// 불리언 타입 -> 숫자 타입
Number(true); // 1
```

---

## 2. Number 프로퍼티

| 프로퍼티                 | 설명                                                              |
| ------------------------ | ----------------------------------------------------------------- |
| Number.EPSILON           | 자바스크립트에서 표현할 수 있는 가장 작은 양수 값과 1 사이의 차이 |
| Number.MAX_VALUE         | 자바스크립트에서 표현할 수 있는 가장 큰 숫자 값                   |
| Nuber.MIN_VALUE          | 자바스크립트에서 표현할 수 있는 가장 작은 숫자 값                 |
| Number.MAX_SAFE_INTEGER  | 자바스크립트에서 안전하게 표현할 수 있는 가장 큰 정수 값          |
| Number.MIN_SAFE_INTEGER  | 자바스크립트에서 안전하게 표현할 수 있는 가장 작은 정수 값        |
| Number.POSITIVE_INFINITY | 양의 무한대                                                       |
| Number.NEGATIVE_INFINITY | 음의 무한대                                                       |
| Number.NaN               | 숫자가 아님을 나타내는 값                                         |

```js
// Number.EPSILON
function isEqual(a, b) {
  // a와 b를 뺀 값의 절대값이 Number.EPSILON보다 작으면 같은 수로 인정
  return Math.abs(a - b) < Number.EPSILON;
}

isEqual(0.1 + 0.2, 0.3); // true

// Number.MAX_VALUE
console.log(Number.MAX_VALUE); // 1.7976931348623157e+308

// Number.MIN_VALUE
console.log(Number.MIN_VALUE); // 5e-324

// Number.MAX_SAFE_INTEGER
console.log(Number.MAX_SAFE_INTEGER); // 9007199254740991

// Number.MIN_SAFE_INTEGER
console.log(Number.MIN_SAFE_INTEGER); // -9007199254740991

// Number.POSITIVE_INFINITY
console.log(Number.POSITIVE_INFINITY); // Infinity

// Number.NEGATIVE_INFINITY
console.log(Number.NEGATIVE_INFINITY); // -Infinity

// Number.NaN
console.log(Number.NaN); // NaN
```

---

## 3. Number 메서드

| 메서드                         | 설명                                                 |
| ------------------------------ | ---------------------------------------------------- |
| Number.isFinite                | 숫자가 유한한지 확인하고 불리언 값으로 반환          |
| Number.isInteger               | 숫자가 정수인지 확인하고 불리언 값으로 반환          |
| Number.isNaN                   | 값이 NaN인지 확인하고 불리언 값으로 반환             |
| Number.isSafeInteger           | 숫자가 안전한 정수인지 확인하고 불리언 값으로 반환   |
| Number.prototype.toExponential | 숫자를 지수 표기법으로 변환하여 문자열로 반환        |
| Number.prototype.toFixed       | 숫자를 고정 소수점 표기법으로 변환하여 문자열로 반환 |
| Number.prototype.toPrecision   | 숫자를 지정된 자릿수로 반올림하여 문자열로 반환      |
| Number.prototype.toString      | 숫자를 문자열로 변환하여 반환                        |

```js
// Number.isFinite
// 인수가 정상적인 유한수이면 true를 반환
console.log(Number.isFinite(10)); // true
console.log(Number.isFinite(Number.MAX_VALUE)); // true

// 인수가 무한수이면 false를 반환
console.log(Number.isFinite(Infinity)); // false
console.log(Number.isFinite(NaN)); // false

// Number.isInteger
console.log(Number.isInteger(10)); // true
console.log(Number.isInteger(10.5)); // false
console.log(Number.isInteger("10")); // false

// Number.isNaN
console.log(Number.isNaN(NaN)); // true
console.log(Number.isNaN("NaN")); // false
console.log(Number.isNaN(undefined)); // false

// Number.isSafeInteger
console.log(Number.isSafeInteger(10)); // true
console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER)); // true
console.log(Number.isSafeInteger(Number.MAX_SAFE_INTEGER + 1)); // false

// Number.prototype.toExponential
console.log((123456).toExponential()); // "1.23456e+5"
console.log((123456).toExponential(2)); // "1.23e+5"

// Number.prototype.toFixed
console.log((123.456).toFixed()); // "123"
console.log((123.456).toFixed(2)); // "123.46"

// Number.prototype.toPrecision
console.log((123.456).toPrecision()); // "123.456"
console.log((123.456).toPrecision(5)); // "123.46"

// Number.prototype.toString
console.log((123.456).toString()); // "123.456"
console.log((123.456).toString(2)); // "1111011.011101"
```

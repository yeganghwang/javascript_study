# 연산자
[MDN 문서](https://developer.mozilla.org/ko/docs/Web/JavaScript/Guide/Expressions_and_operators)
---
연산자란...
> 데이터에 연산을 수행하고 값을 조작하며, 변수에 값을 할당하거나 비교하고 논리적인 판단을 내리는 데 사용되는 기호. `산술` 연산자, `비교` 연산자, `논리` 연산자, `할당` 연산자가 있다.
## 산술 연산자
1. `+` 더하기
2. `-` 빼기
3. `*` 곱하기
4. `/` 나누기
5. `%` 나머지 연산
6. `**` 거듭제곱 연산
 ```javascript
  let sum = 5 + 3;       // 8
  let diff = 5 - 3;      // 2
  let product = 5 * 3;   // 15
  let quotient = 5 / 3;  // 1.6666666666666667
  let remainder = 5 % 3; // 2
  let power = 5 ** 3;    // 125
  ```

## 비교 연산자
1. `==` : 동등 비교(느슨한 동등 비교, 약한 비교, Loose Equality)
2. `===` : 일치 비교(엄격한 일치 비교, 강한 비교, Strict Equality)
3. `>`, `>=` : 초과 비교, 이상 비교
4. `<`, `<=` : 미만 비교, 이하 비교
```javascript
let looseEquality = 5 == "5";     // true
let strictEquality = 5 === "5";   // false
let greater = 5 > 3;              // true
let greaterEqual = 5 >= 5;        // true
let less = 5 < 5;                 // false
let lessEqual = 5 <= 5;           // true
```


## 논리 연산자
논리(참, 거짓)을 구분하기 위한 연산자이다. `AND`, `OR`, `NOT` 등이 있다.
JavaScript 에서는 `&&` 와 `||` 이 갖는 특별한 기능이 있다. 문서참조
1. [`&&`](./and_or.md) : AND 연산자. 좌항과 우항의 논리갑싱 모두 `true` 라면 `true`, 아니면 `false`를 반환한다.
2. [`||`](./and_or.md) : OR 연산자. 좌항의 논리값 중 하나 이상의 값이 `true` 라면 `true`, 하나라도 `true` 가 아니라면 `false`를 반환한다.
``` javascript
console.log( (5 > 3) && isNaN("one") );  // true
console.log( false && (3 < 7) );         // false
```

## 할당 연산자
할당 연산자 `=` 우측의 값을 할당 연산자 좌측으로 대입할 때 사용한다.
다른 연산자와 함께하여 사용할 수도 있다.
1. `=` : 연산자 우측의 값을 좌측에 할당한다.
2. `+=` : 연산자 좌측의 값에서 우측의 값을 더한 다음 좌측에 할당한다. ( left = left + right; )
3. `-=` : 연산자 좌측의 값에서 우측의 값을 뺀 다음 좌측에 할당한다. ( left = left - right; )
4. `*=` : 연산자 좌측의 값에서 우측의 값을 더한 다음 좌측에 할당한다. ( left = left * right; )
5. `/=` : 연산자 좌측의 값에서 우측의 값을 나눈 다음 좌측에 할당한다. ( left = left / right; )

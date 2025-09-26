# 화살표 함수
함수 선언을 간단히 할 수 있다.
## 사용법
```js
let add = function (a, b) {
  return a + b;
}
```
- `add` : 함수 표현식을 담은 변수의 이름
- `(a, b)` : 매개 변수
- `{}` : 코드 블록
- `return` : 반환

이 [함수 표현식](./expression.md)를 다음과 같이 간단히 할 수 있다.
```js
let add = (a, b) => { return a + b; }
```
함수의 내용이 한 줄이라면 `{}` 중괄호를 생략할 수 있다.
```js
let add = (a, b) => console.log(+a + +b);
```
- `add` : 함수 표현식을 담은 변수의 이름
- `(a, b)` : 매개 변수
- `=>` : 화살표 기호
- `{}` : 코드 블록 (한 줄의 코드인 경우 생략 가능)

`return` 문의 경우 중괄호 없이 작성하면 오류가 발생하나,
중괄호가 없는 경우 `return`문을 생략할 수 있다.
```js
let add = (a, b) => return a + b; // ERROR: Unexpected token 'return'
let add = (a, b) => a + b; // ok
```

---
화살표 함수는 [콜백 함수](./callback.md)와 함께 사용하는 경우 함수의 표현을 더욱 간단하고 명확히 할 수 있다.
기존의 `function` 키워드를 이용한 콜백 함수의 경우는 아래와 같다.
```js
let arr = [1, 3, 9];
let arr2 = [];

arr.forEach( function (element) {
  arr2.push(element * 2);
});
```
그러나 화살표 함수를 이용하면 아래와 같이 가독성을 유지한 채로 코드를 간결하게 만들 수 있다. 
```js
let arr = [1, 3, 9];
let arr2 = [];
arr.forEach( element => arr2.push(element * 2) );
```
## 화살표 함수의 this
화살표 함수는 다른 함수와 달리 '고유한' `this`를 가지지 않는다.
따라서 화살표 함수 내에서 `this`를 사용하면, 화살표 함수 내부의 `this` 값이 아닌 외부의 `this` 값을 가져온다.
```js
let user = {
  name: "Yegang Hwang",
  sayHi() {
    let arrow = () => console.log(this.name);
    arrow();
  },
  sayHello() {
    let fn = function() { console.log(this.name); };
    fn();
  }
}

user.sayHi(); // Yegang Hwang
user.sayHello(); // undefined
```

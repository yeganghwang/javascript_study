# 객체
`key-value` 를 담는 자료형이다. `중괄호{}`를 이용하여 선언할 수 있고, `콜론 : `좌측에 프로퍼티 이름(key), 우측에 값(value)를 지정할 수 있다.
key는 문자열 혹은 심볼이어야 한다. 문자열이 아니라면 문자열로 변환된다.
```js
let user = {
  name: "John",
  surname: "Doe",
  age: 24
};
```
이렇게 객체를 선언한 다음, `점 연산자(.)` 혹은 `대괄호`를 이용하여 객체 내의 항목에 접근할 수 있다.
```js
console.log(user.name);    // John
user.name = "Yegang";
console.log(user.name);    // Yegang
console.log(user["name"]); // Yegang
```
`in` 연산자로 프로퍼티의 존재 여부를 알 수 있다.
```js
console.log( "age" in user );    // true
console.log( "isMale" in user ); // false
```
`for...in` 반복문으로 객체를 순환할 수 있다.
```js
for (let key in user) {
  console.log(key);        // name surname age
  console.log(user[key]);  // Yegang Doe 24
}
```
`delete` 연산자로 객체의 프로퍼티를 삭제할 수 있다.
```js
delete user.surname;
```
## 객체 메서드와 `this`
객체 안에 메서드를 만들 수 있다.
```js
function sayHi() {
  console.log("Hi!");
}

let user = {
  name: "John",
  age: 13,
  sayHi: sayHi
};

user.sayHi(); // 메서드 호출
```
또한 메서드 내부에서 `this` 키워드를 사용하면 객체에 접근할 수 있다.
점 앞의 `this`는 객체를 나타낸다.
`this`는 다른 언어와 달리 모든 함수에서 사용할 수 있다.
```js
function sayHi() {
  console.log("my name is " + this.name);
}
user.sayHi = sayHi;
user.sayHi(); // my name is John
```
화살표 함수 안에서 `this`를 사용하면 화살표 함수 바깥에 있는 외부 함수에서 `this`값을 가져 온다.
```js
name = "John External";  // 외부 전역 환경
const hello = () => console.log("My arrow-function name is " + this.name);

let user = {
  name: "John Internal",
  age: 15,
  hello: hello  
}

user.hello();    // My arrow-function name is John External
```


## `new` 연산자와 생성자 함수
## 옵셔널 체이닝 `?.`
## 심볼
## 객체를 원시형으로 변환

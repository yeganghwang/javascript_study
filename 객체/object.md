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
생성자 함수는 일반 함수와 거의 같은데, `new` 연산자를 붙여서 실행한다. 그리고 함수의 첫 글자가 대문자이다. 소문자여도 생성자 함수를 실행할 수 있지만 일반 함수와 생성자 함수를 구분하기 위하여 생성자 함수의 첫 글자는 대문자를 사용한다.
`new` 연산자를 사용하면 암시적으로 `this` 객체가 만들어지고 `this`를 반환한다.
```js
function User(name) {
  this.name = name;
  this.isAdmin = false;
}
반환문도 존재하지 않고 `this` 객체도 없지만 실제로는 `this` 객체를 암시적으로 만든 후 반환한다.
```js
function User(name) {
  this = {};
  this.name = name;
  this.isAdmin = false;
}
```
이렇게 `this` 객체를 암시적으로 만든 후 반환한다.
이렇게 만들어진 생성자는 `new` 연산자를 붙여서 실행한다.
```js
let user1 = new User("황예강");
let user2 = new User("홍길동");
let user3 = new User("John Doe");
```
### 생성자의 `return`문
생성자 함수에는 return문이 없다. 반환해야 할 것은 this에 저장되고 this가 반환되기 때문이다.
그러나 `return`문 뒤에 객체가 오면 생성자는 해당 객체를 반환하고, 원시형을 반환한다면 해당 `return`문이 무시된다.
1. return문이 있고, 객체를 반환하는 경우
   ```js
   function Test() {
     let obj = {name: "객체"};
     this.name = "황예강";

     return obj;
   }
   test = new Test();
   console.log(test.name);
   ```
   결과 : `객체`
2. return문이 있고, 일반 자료형을 반환하는 경우
   ```js
   function Test() {
     let myNewName = "홍길동";
     this.name = "황예강";

     return myNewName;  // 원시형을 반환하기에 무시된다.
     //return this; 가 실행된다.
   }
   ```
   결과 : `황예강`
### 생성자 내의 메서드
생성자 안에 있는 함수는 메서드라고 부른다.
```js
function User(name) {
  this.name = name;
  this.sayHello = function () {
    console.log(`안녕하세요, 제 이름은 ${this.name} 입니다.`);
  };
}

let user = new User("황예강");
let user2 = new User("홍길동");
user.sayHello();
user2.sayHello();
```
## 옵셔널 체이닝 `?.`
## 심볼
## 객체를 원시형으로 변환

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
## 옵셔널 체이닝
### `?.`
```js
let user = {};
console.log(user.address.street); // 에러 발생
console.log(user.address?.street); // undefined
```
존재 여부가 확실하지 않은 값을 에러 없이 확인할 수 있다.
빈 객체 `user`에는 `address` 프로퍼티가 존재하지 않은데(undefined), undefined의 하위 프로퍼티인 `street`을 찾으려고 하는 경우 아래와 같은 에러가 발생한다.
```js
Uncaught TypeError: Cannot read properties of undefined (reading 'street')
```
`?.` '앞'의 평가 대상이 `undefined`나 `null`인 경우 평가를 멈추고 `undefined`를 반환하므로 에러가 발생하지 않는다.
즉 `user.address?.street`에서 `user.address`가 `undefined`이므로 뒤의 프로퍼티 `street`을 평가하지 않고 `undefined`를 반환한다.

### `?.()`
존재 여부가 확실하지 않은 함수를 호출할 수 있다.
존재한다면 실행하고, 존재하지 않다면 아무 일도 일어나지 않는다.
```js
let user1 = {
  admin() {
    console.log("관리자 계정입니다.");
  }
}
let user2 = {};

user1.admin?.(); // admin 실행
user2.admin?.(); // 아무 일도 일어나지 않는다.
```

### `?.[]`
객체 존재 여부가 확실하지 않은 경우에도 안전하게 프로퍼티를 읽을 수 있다.
```js
let user1 = { firstName: "Violet" };
let user2 = null;
let key = "firstName";

alert( user1?.[key] ); // Violet
alert( user2?.[key] ); // undefined
alert( user1?.[key]?.something?.not?.existing); // undefined
```
## 심볼
심볼은 유일한 식별자를 생성할 때 사용한다.
```js
let id = Symbol("아이디"); // 설명(심볼 이름)이 "아이디"
console.log(id.toString()); // 'Symbol("아이디")'
console.log(id.description); // '아이디'
```
### 숨김 프로퍼티
외부 코드에서 접근이 불가능한 프로퍼티이다.
```js
let user = { name: "John" }; // 이 객체에 함부로 프로퍼티를 추가할 수 없을 때
let id = Symbol("id"); // 심볼을 이용하여
user[id] = 1; // 숨김 프로퍼티를 만들 수 있다.
console.log(user[id]); // 1. 외부에서 접근이 불가능하다.
```
객체 리터럴`{...}`으로 객체를 만든 경우에는 대괄호를 사용한다.
숨김 프로퍼티는 `for...in`에서 배제되며,
`Object.assign()`을 이용하여 복사하는 경우에는 복사된다.
```js
let id = Symbol("id");
let user = {
  name: "John",
  [id] : 123
};

for (let i in user) {
  console.log(`${i}: ${user[i]}`); // name: "John" 만 출력된다. id는 숨김 프로퍼티이므로 출력되지 않는다.
}

let obj = Object.assign({}, user); // user 객체를 복사하여 obj에 저장
console.log(obj); // { name: 'John', id: 123, [Symbol(id)]: 1 } 모두 다 복사된다.
```
## 객체를 원시형으로 변환
원시값을 기대하는 내장 함수나 연산자를 사용할 때 형 변환은 자동으로 일어난다.

이 때 `hint`라 불리는 값이 구분의 기준이 된다. ‘목표로 하는 자료형’이다.

- `"string"` 문자열을 기대하는 연산을 수행할 때는 hint가 `string`이 된다.
- `"number"` 수학 연산을 적용하려 할 때 hint는 `number`가 된다.
- `"default"` 연산자가 기대하는 자료형이 확실치 않을 때 `default`가 된다.
    - `+`는 두 문자열을 합치는 연산을 할 수도 있고 두 숫자를 더하는 연산도 할 수 있기에, `+`의 인수가 객체인 경우에는 hint가 `default`가 된다.
    - `==`를 사용해 객체-문자형, 객체-숫자형, 객체-심볼형끼리 비교할 때도 객체를 어떤 자료로 바꿔야 할 지 확신이 안 서므로 hint는 defulat가 된다.

`Symbol.toPrimitive`라는 내장 심볼이 존재한다. 이 심볼은 hint를 명명하는 데 사용된다.

```jsx
let user = {
	name: "John",
	money: 1000,
	
	[Symbol.toPrimitive](hint) {
		console.log("hint : " + hint);
		return hint == "string" ? `{name: "${this.name}"}` : this.money;
		}
	};
	
	console.log(user); // hint : string -> {name: "John"}
	console.log(+user); // hint : number -> 1000
	console.log(user + 500); // hint : default -> 1500
```

또는 구식의 방법이지만 아래의 방법을 사용할 수도 있다. 본래 `toString()`은 ‘[object Object]’를 반환하고, `valueOf()`는 객체 자신을 반환하는데, 이 메서드들을 사용해서 형 변환을 구현할 수도 있다.

```jsx
let user = {
	name: "johnson",
	age: 30,
	
	toString() {
		return this.name;
	}
	
	valueOf() {
		return this.age;
	}

console.log(String(user)); // johnson
console.log(Number(user)); // 30
```

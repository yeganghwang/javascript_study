# new Function
`new Function` 문법을 이용하면 함수를 만들 수 있다.
```js
let func = new Function([arg1, arg2, ..., argN], functionBody);

let sum = new Function('a', 'b', 'return a + b');
console.log( sum(1,5) ); // 6
```

새로 만들어지는 함수는 인수(`arg1, arg2...argN`)과 함수 본문 `functionBody`로 구성된다. 인수는 생략 가능하다.
```js
let sayHi = new Function('alert("HELLO")');
sayHi(); // HELLO
```

기존의 함수 표현식, 함수 선언문과 달리 `new Function`을 이용하면 런타임때 받은 문자열로 함수를 만들 수 있다.

함수는 특별한 프로퍼티 `[[Environment]]` 에 저장된 정보를 이용해 자기 자신이 태어난 곳을 기억하는데,
`[[Environment]]`는 함수가 만들어진 렉시컬 환경을 참조한다.
그런데 `new Function`을 통해 함수를 만들면 함수의 `[[Environment]]`프로퍼티가 현재 렉시컬 환경이 아닌 전역 렉시컬 환경을 참조하게 된다.
따라서 외부 변수에 접근할 수 없고, 전역 변수에만 접근할 수 있다.

```js
function getFunc() {
	let value = 'text';
	
	let func = new Function('console.log(value)');
	
	return func;
}

getFunc()(); // value is not defined


function getFunc2() {
	let value = 'text';
	
	let func2 = () => console.log(value);
	
	return func2;
}

getFunc2()(); // text
```

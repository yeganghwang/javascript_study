# 함수 표현식(Function Expression)
함수는 식으로 표현되어 변수나 상수에 할당되는 것이 가능하다.
``` javascript
let sayHi = function() {
  console.log('hello, world!');
}
```

또한 변수를 복사해 또 다른 변수에 할당하는 것도 가능하다.
```javascript
let func = sayHi;
func(); // hello, world!
sayHi(); // hello, world!
```
함수 선언문은 함수 선언문이 정의되기 전에도 실행이 가능한 반면, 함수 표현식은 실제 실행 흐름이 함수에 도달하였을 때 사용 가능하다.
``` javascript
console.log( add(3,5) ); // 실행됨
function add(a, b) { // 선언문이 아래에 있더라도 
  return a + b;
}
```

``` javascript
console.log( mul(3,5) ); // 실행 안 됨
const mul = function(a, b) { // 실행 흐름이 함수 표현식에 도달하기 이전이므로
  return a * b;
}
```

## 기명 함수 표현식(Named Function Expression)
기명 함수 표현식은 이름이 있는 함수 표현식이다. 이전의 함수 표현식은 익명 함수이다.
이름이 붙어도 여전히 함수 표현식을 할당한 형태이기 때문에 함수 선언문이 되지는 않는다.
다만 이름을 사용해 함수 표현식 내부에서 자기 자신을 참조할 수 있다.
기명 함수 표현식 외부에서는 이름을 사용할 수 없다.
아래와 같이 사용한다.
```js
let sayHi = function func(who) {
  if (who) {
    alert(`Hello, ${who}`);
  } else {
    func("Guest"); // func를 사용해서 자기 자신을 호출함.
  }
};

sayHi("John");  // Hello, John
sayHi();        // Hello, Guest
func();         // 기명 함수 바깥에서는 이름을 사용할 수 없다.
```

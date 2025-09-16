# 함수 표현식
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

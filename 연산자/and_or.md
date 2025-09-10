# '&&'(AND), '||'(OR)
## '&&'
AND 연산자로, 피연산자를 오른쪽으로 평가하면서 `falsy`한 값을 만나면 즉시 그 값을 반환하고,
모든 값이 `truthy`하다면 마지막 값을 반환한다.
|입력1|입력2|출력|
|---|---|---|
|false|false|false|
|false|true|false|
|true|false|false|
|true|true|true|

좌측 값이 `falsy`하다면, 우측의 값은 평가조차 되지 않는다.
``` javascript
function printHelloAndReturnTrue() {
  console.log("Hello World");
  return true;
}

if ( 1 && printHelloAndReturnTrue() ) {}; // "Hello World", true
if ( 0 && printHelloAndReturnTrue() ) {}; // 출력 안 됨, false
```

또한 좌측 값이 truthy하고, 우측 값이 falsy하다면, 우측의 값을 반환한다.
``` javascript
console.log( printHelloAndReturnTrue() && NaN ); // "Hello World", NaN
console.log( true && undefined ); // undefined
```

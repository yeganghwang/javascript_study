## 숫자형 (Number)
``` js
let billion = 1000000000;
let billion2 = 1e9; // 1 * 10^9

console.log(0xff); // 255
console.log(0b00101010); // 2진법 00101010 = 42 출력
console.log(0b00101010 === 42); // true

let num = 255;
console.log( num.toString(16) ); // 'ff'
console.log( num.toString(2) ); // '11111111'
console.log( 255..toString(2) ); // '11111111'
```

### 올림, 내림, 반올림 등
- `Math.floor()` 자연수로 내림
- `Math.ceil()` 자연수로 올림
- `Math.round()` 자연수로 반올림
- `Math.trunc()` 소숫점을 버림
```js
let num = 3.14;
console.log( Math.round(num*10) / 10); // 3.1
num = 3.98931;
console.log( Math.round(num*10) / 10); // 4  
```

||`Math.floor()`|`Math.ceil()`|`Math.round()`|`Math.trunc()`|
|--|--|--|--|--|
|1.1|1|2|1|1|
|1.7|1|2|2|1|
|-1.3|-2|-1|-1|-1|
|-1.7|-2|-1|-2|-1|

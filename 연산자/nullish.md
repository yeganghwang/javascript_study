# '??' (nullish 병합 연산자)
피연산자 값 중 **값이 확정되어 있는** 변수를 찾을 수 있는 기능이다.
```javascript
x = (a !== null && a !== undefined) ? a : b; // x = b
x = a ?? b; // x = b
```
[OR 연산자](./and_or.md)와의 다른 점은 OR 연산자는 첫 번째 truthy한 값을 반환하는 반면,
?? 연산자는 첫 번째 확정된 값을 반환한다.

```javascript
let delayTime = 0;
console.log(delayTime || 100); // 100
console.log(delayTime ?? 100); // 0
```

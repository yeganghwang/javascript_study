# 함수 선언
함수 선언(function declaration) 방식을 이용하여 함수를 만들 수 있다.
```javascript
function calculateCircleArea(radius) {
  const pi = 3.14159
  const area = radius * radius * pi;
  return area; 
}
```
`function` 키워드, 함수 이름, 괄호로 둘러싼 매개변수를 차례로 작성하여 함수를 선언할 수 있다.
이어서 함수를 구성하는 코드의 모임인 함수 본문을 중괄호로 감싸 붙여준다.
```javascript
function 함수이름(매개변수1, 매개변수2) { ...함수 본문 }
```
새롭게 정의한 함수는 함수 이름 옆에 괄호와 매개변수를 붙여 사용할 수 있다.
```javascript
const r = 7;
const area = calculateCircleArea(r);
console.log(area); // 153.93791
// 여러 번 반복하여 함수 사용 가능
const r2 = 6;
const area2 = calculateCircleArea(r);
console.log(area2);
```

## 지역 변수
함수 내에서 선언한 변수인 지역 변수는 함수 내에서만 접근할 수 있고, 외부에서는 접근이 불가능하다.
```javascript
function calculateCircleArea(radius) {
  const pi = 3.14159;
  const area = radius * radius * pi;
  return area;
}

console.log(area); // area is not defined
```

## 외부 변수
함수 내부에서는 함수 외부의 변수인 외부 변수(outer variable)에 접근할 수 있다.
```javascript
let userName = 'Yegangs';
function showMessage() {
  let message = 'Hello, ' + userName;
  alert(message);
}

showMessage(); // Hello, Yegangs
```
또한 외부 변수를 수정하는 것도 가능하다.
```javascript
let userName = 'Yegangs';
function showMessage() {
  userName = 'Dominic'; // 외부 변수를 수정함
  let message = 'Hello, ' + userName;
  alert(message);
}
alert(userName); // 함수 호출 전이므로 Yegangs가 출력됨
showMessage(); // Hello, Dominic
alert(userName); // 함수에 의해 Dominic으로 값이 바뀜
```
함수 외부에서 선언된 변수의 이름과 같은 이름의 변수가 내부에서 선언된 경우, 내부 변수는 외부 변수를 가린다. 내부에서 해당 변수를 수정하더라도 외부 변수는 내부 변수에 의해 가려져 값이 수정되지 않는다.
```javascript
let userName = 'Simon';
function showMessage() {
  let userName = 'Dominic';
  let message = 'Hello, ' + userName; // Dominic
  alert(message);
}

//함수는 내부 변수인 userName만 사용한다.
showMessage(); // Dominic
alert(userName); // Simon, 함수는 외부 변수에 접근하지 않았으므로 값이 변경되지 않고 Simon이 출력된다.
```
## 매개 변수
## 기본 값
## 반환 값
## 함수 네이밍
## 함수 주석

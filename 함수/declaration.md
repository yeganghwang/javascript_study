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
매개변수(parameter)를 이용하면 임의의 데이터를 함수 안에 전달할 수 있다.
```javascript
function showMessage(from, text) {
  alert(from + ' : ' + text);
}

showMessage('Yegang', 'Hello!');   // Yegang : Hello!
showMessage('Simon', 'What\'s up?');// Simon : What's up?
```
매개변수는 함수 선언방식 괄호 사이에 있는 변수이고, (`from`, `text`) 
인수는 함수를 호출할 때 매개변수에 전달되는 값이다. (`'Yegang'`, `'Simon'`, `'Hello!'`, `'What\'s up?'`)
## 기본 값
함수 호출 시 매개변수에 인수를 선언하지 않으면 그 값은 `undefined`가 된다.
매개변수에 값을 전달하지 않아도 그 값이 undefined가 되지 않게 하려면 함수를 선언할 때 `=`를 사용해 기본값(default value)를 설정하면 된다.
```javascript
function showMessage(from, text = 'no text given') {
  alert( from + ' : ' + text );
}
showMessage('Hwang'); // Hwang : no text given
```

매개변수에 값을 전달해도 그 값이 `undefined`라면 기본값이 할당된다.
```javascript
showMessage('Yegang', undefined); // Yegang : no text given
```
함수의 표현도 기본값으로 설정할 수 있다.
```javascript
function showMessage(from, text = anotherFunction()) {
  // anotherFunction()은 text의 값이 undefined일 때만 호출된다.
  // anotherFunction()의 반환 값이 text가 된다.
}
```

## 반환 값
지시자 `return`을 이용하여 함수를 호출한 곳에 특정한 값을 반환할 수 있다. 실행의 흐름이 지시자 `return`을 만나면 함수의 실행은 즉시 중단되고 함수를 호출한 곳에 값을 반환한다. 함수 하나에 여러 개의 `return`문이 있을 수 있다. (조건과 분기에 따라)
## 함수 네이밍
함수는 **특정한 동작**을 수행하기 위해 코드를 모아놓은 것이다. 따라서 함수의 이름은 **동사**가 적합하다. 함수의 이름은 가능한 한 간결하고 명확하고, 어떤 동작을 하는지 쉽게 알 수 있어야 하며, 그 뜻이 합의된 접두어만 사용하여야 한다.
예를 들어 `"show"`로 시작하는 함수는 대개 무언가를 보여주는 함수이다.
함수는 동작 하나만 담당해야 한다. 한 장소에서 두 동작을 필요로 하는 경우에도 동작 하나만 담당해야 하므로 함수를 분리한다.
## 함수 주석
함수를 설명하는 기능을 작성한다.
`JSDoc`을 이용하면 IDE에서 함수의 매개변수, 반환값 등을 쉽게 확인할 수 있다.

```javascript
/**
 * 신장과 체중을 입력받아 bmi를 반환하는 함수
 * @param {number} height cm단위의 신장
 * @param {number} weight kg단위의 체중
 * @return {number} bmi 지수
*/
function calculateBmi(height, weight) {
  const meter_height = height / 100;
  return ( weight ) / ( meter_height) ** 2;
}

```

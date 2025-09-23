# 콜백 함수
함수를 함수의 인수로 전달하고, 인수로 전달한 그 함수를 나중에 호출(call back)하는 것이다.
```js
function ask(question, yes, no) {
  if (confirm(question)) {
    yes();
  } else {
    no();
  }
}

function showOk() {
  alert('동의하셨습니다.');
}

function showCancel() {
  alert('취소하셨습니다.');
}

ask('동의하십니까?', showOk, showCancel);
```
위 코드에서 `ask`는 매개변수로 `question`, `yes`, `no`를 받는데, 이들은 함수이다.
`showOk`, `showCancel`을 인수로 호출한다. 또는 아래와 같이 **익명 함수**로도 호출이 가능하다.
```js
ask('동의하십니까?',
  function () { alert('동의하셨습니다.'); },
  function () { alert('취소하셨습니다.'); });
```
이와 같이 함수의 이름이 정해지지 않은 함수를 `익명 함수`라고 한다.

## setTimeout
`setTimeout`은 특정 시간이 지난 후 함수를 실행시킨다.
```js
showTimeout(함수, 밀리세컨드);
```
함수를 인수로 전달하므로 콜백 함수이다.
```js
function showHello() {
  console.log('Hello, World!');
}

setTimeout(showHello, 3000); // 3000ms 후 showHello() 실행
```

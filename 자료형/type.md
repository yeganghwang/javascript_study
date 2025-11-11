

## 문자열형

`''` , `""` , ```` 사용 가능. 특수 문자는 이스케이프 문자 (`\`) 붙여서 `\"` 와 같이 사용.

- 문자열의 길이 : `str.length`
- 문자열의 인덱스 : `str[index]` 또는 `str.charAt(index)`  index는 음수일 수 있음. `-1` 은 마지막 문자
- 문자열 바꾸기
    
    ```jsx
    let str = "Qi, My name is Yegang Hwang";
    str = str.replace(/Qi/gi, "Hi"); // 대소문자를 구분하지 않고(i) 모든(g) Qi를 변경
    ```
    
- 대소문자 변경 : `str.toUpperCase()` , `str.toLowerCase()` 또는 `str[0].toUpperCase()`
- 부분 문자열 찾기
    
    `indexOf()` 문자열의 위치를 반환. `-1` 의 경우 찾지 못함을 뜻함.
    
    ```jsx
    let str = "Widget with id";
    console.log(str.indexOf("Widget")); // 0
    console.log(str.indexOf("hello")); // -1
    console.log(str.indexOf("id")); // 1 <= W'id'get
    console.log(str.indexOf("id", 2)); // 12 <= 두번째로 만나는 문자열
    ```
    
    또는 `includes()` 는 true/false 를 반환
    
    ```jsx
    str.includes("Widget"); // true
    str.includes("hello"); // false
    str.includes("id", 3); // false
    ```
    
    문자열의 시작(`startsWith()`), 끝(`endsWith()`) 검사 : true / false 반환
    
    ```jsx
    str.startsWith("Wi"); // true
    str.endsWith("d"); // true
    ```
    
- 문자열 추출하기
    
    `str.slice(start [, end])` start부터 end까지(end는 미포함) 문자열을 반환
    
    ```jsx
    let str = "stringify";
    console.log( str.slice(0, 5) ); // strin
    console.log( str.slice(0, 1) ); // s
    console.log( str.slice(3, 6) ); // ing
    ```
    
    `str.substring(start [, end]` start와 end **사이**에 있는 문자열 반환
    
    ```jsx
    let str = "stringify";
    console.log( str.substring(2, 6) ); // ring
    console.log( str.substring(6, 2) ); // ring
    ```
    
    `str.substr(start [, length]` start부터 **length개만큼의 글자**를 반환
    
    ```jsx
    let str = "stringify";
    console.log( str.substr(4, 2) ); // ng
    ```
    

## 배열

타 언어와 마찬가지로 배열을 선언할 때 `[]` 로 선언하거나 `new Array()` 로 선언할 수 있다.

```jsx
let fruits = ['apple', 'orange', 'pear'];
let arr = new Array(1, 2, 3); // [1, 2, 3]
```

- 배열 조작 함수
    - `push()` 배열 마지막에 요소를 추가하고 `length` 를 반환한다. 여러 개를 추가할 수도 있다. **Stack**
        
        ```jsx
        fruits.push('strawberry'); // 4
        console.log(fruits); // ['apple', 'orange', 'pear', 'strawberry']
        ```
        
    - `pop()` 배열 마지막의 요소를 제거하고 해당 요소를 반환한다. **Stack**
        
        ```jsx
        fruits.pop(); // 'strawberry'
        console.log(fruits); // ['apple, 'orange', 'pear']
        ```
        
    - `unshift()` 배열 처음에 요소를 추가하고 `length` 를 반환한다. 여러 개를 추가할 수도 있다. **Queue**
        
        ```jsx
        fruits.unshift('mango') // 5
        console.log(fruits); // ['mango', 'apple', 'orange', 'pear']
        ```
        
    - `shift()` 배열 처음의 요소를 제거하고 해당 요소를 반환한다. **Queue**
        
        ```jsx
        fruits.shift(); // mango
        console.log(fruits); // ['apple', 'orange', 'pear']
        ```
        
    - `splice()` 배열의 특정 요소를 삭제한다.
        
        ```jsx
        fruits.splice(1, 1); // index 1부터 1개의 요소 제거 ['apple', 'pear']
        
        // splice(start, deleteCount, 요소1, 요소2...) 요소로 변경
        let arr = ['I', 'stury', 'JavaScript', 'right', 'now'];
        arr.splice(0, 3, 'Lets', 'dance'); // ['Lets', 'dance', 'right', 'now']
        ```
        
    - `slice(start, end)` start부터 end를 제외한 end까지 요소를 복사한 새로운 배열을 반환
    - `concat(arg1, arg2...)` 인수를 포함하여 새로운 배열을 반환한다.
        
        ```jsx
        let arr1 = [1, 2, 3];
        let arr2 = arr1.concat(4, 5, 6); // [1, 2, 3, 4, 5, 6]
        let arr3 = arr2.concat(arr1); // [1, 2, 3, 4, 5, 6, 1, 2, 3]
        ```
        
- 배열 변형 함수
    - `map(fn)` : 함수를 호출하고 함수 호출 결과를 배열로 반환한다.
        
        ```jsx
        let npcs = ["Bilbo", "Gandalf", "Nazgul"].map(item => item.length);
        console.log(npcs); // [5, 7, 6]
        ```
        
    - `sort(fn)` : 배열 내부 요소를 정렬한다. 요소는 문자열로 취급되어 정렬된다.
        
        ```jsx
        let arr = [1, 2, 15];
        arr.sort();
        console.log(arr); // [1, 15, 2] <- 문자열 취급
        ```
        
        문자열이 아닌 경우 새로운 정렬 기준을 만들어서 사용해야 한다.
        
        ```jsx
        function compareNumeric(a, b) {
        	if (a > b) return 1;
        	if (a == b) return 0;
        	if (a < b) return -1;
        }
        
        let arr = [1, 2, 15];
        arr.sort(compareNumeric);
        ```
        
    - `reverse()` : 역순으로 바꿔주는 함수
        
        ```jsx
        let arr = ['apple', 'orange', 'pear'];
        arr.reverse();
        
        console.log(arr); // ['pear', 'orange', 'apple']
        
        ```
        
    - `split(구분자)` : 구분자를 기준으로 문자열을 배열에 저장
        
        ```jsx
        let names = '홍길동, 황예강, 임꺽정';
        let arr = names.split(', '); // 구분자를 ', ' 으로 지정하여 split
        console.log(arr); // ['홍길동', '황예강', '임꺽정'] 
        ```
        
- 배열 순회
    - `forEach()`로 반복작업 하기
        
        ```jsx
        let arr = ['John', 'James', 'Jane', 'Jacob'];
        arr.forEach(function (item, index, array) {
        	console.log(`${item} is at index ${index} in ${array}`);
        });
        ```
        
    - array[index] 로 순회 가능
    - for ( let item of array) 로 순회 가능
- 배열 정보 함수
    - `indexOf(item, from)` : 인덱스 from 부터 item을 찾아 index를 반환. 없으면 -1 반환
    - `lastIndexOf(item, from)` : `indexOf()` 와 같으나 뒤에서부터 검색 시작
    - `includes(item, from)` : 인덱스 from 부터 item을 찾아 true/false 반환
    - `find(fn)` : 함수가 참을 반환하면 해당 요소가 반환된다.
        
        ```jsx
        let users = [
        	{id: 1, name: "John"},
        	{id: 2, name: "Pete"},
        	{id: 3, name: "Mary"},
        ];
        
        let user = users.find(item => item.id == 1);
        console.log(user); // {id: 1, name: "John"}
        
        let user2 = users.findIndex(item => item.id == 3);
        console.log(user2); // 2	
        ```
        
    - `filter(fn)` 함수가 참을 반환하는 여러 개의 요소를 찾아 배열로 반환한다.
        
        ```jsx
        let user3 = users.filter(item => item.id < 3);
        console.log(user3); // [{id: 1, name: "John"}, {id: 2, name: "Pete"}]
        ```
        

## iterable

1. 이터러블은 반복 가능하다는 뜻으로, 이터러블을 사용하면 어떤 객체든 `for...of` 반복문을 사용할 수 있다.
2. `for...of` 는 `[Symbol.iterator]()` 를 호출하고, 해당 메서드는 반드시 `next()`  를 반환해야 한다.
3. `next()` 의 반환 값은 `{ done:false, value:any }` 같은 형식이어야 한다. `done=true` 는 반복문이 종료되었음을 뜻한다.
4. 문자열은 이터러블이다. `for ... of` 로 문자열을 순회할 수 있다.

### 예시

```jsx
let range = {
  from: 1,
  to: 5
};

range[Symbol.iterator] = function() {
  return {
    current: this.from,
    last: this.to,
    next() {
      if (this.current <= this.last) {
        return { done: false, value: this.current++ };
      } else {
        return { done: true };
      }
    }
  };
};

for (let num of range) {
  alert(num); // 1, then 2, 3, 4, 5
}
```

- 또는 아래와 같이 작성할 수도 있다.
    
    ```jsx
    let range = {
    	from:1,
    	to:5,
    	
    	[Symbol.iterator]() = function () {
    		this.current = this.from;
    		return this;
    	},
    	
    	next() {
    		if (this.current <= this.to) {
    			return { done: false, this.current ++ };
    		} else {
    			return {done: true};
    		}
    };
    
    for (let num of range) {
    	console.log(num); // 1, 2, 3, 4, 5
    }
    ```
    

### 이터레이터를 명시적으로 호출

```jsx
let str = "Hello";

let iterator = str[Symbol.iterator]();

while (true) {
	let result = iterator.next();
	if(result.done) break;
	console.log(result.value); // 글자가 하나씩 출력됨
}
```

iterator를 지정하여 호출하는 경우는 거의 없는데, for…of 방법을 사용하는 것보다 반복 과정을 더 잘 통제할 수 있다. 반복을 시작했다가 잠시 멈춰 다른 작업을 하다가 다시 반복을 시작하는 것과 같이 반복 과정을 여러 개로 쪼개는 것이 가능하다.

### Array.from()

Array.from()은 이터러블이나 유사 배열을 진짜 배열로 만들어 준다.

유사 배열은 인덱스와 `length` 프로퍼티가 있어서 배열처럼 보이는 객체고, 이터러블은 `Symbol.iterator` 메서드가 구현된 객체이다.

```jsx
let range = {
	from: 1,
	to: 5,
	
	[Symbol.iterator]() = function () {
		this.current = this.from;
		return this;
	},
	
	next() {
		if (this.current <= this.to) {
			return { done: false, this.current++ };
		} else {
			return { done: true };
		}
	}
}

let arr = Array.from(range);
console.log(arr.pop()); // world
```

매핑 함수를 선택적으로 넘겨줄 수도 있다.

```jsx
Array.from(obj[, mapFn, thisArg]);

// 각 숫자를 제곱
arr = Array.from(range, num => num * num);
console.log(arr); // 1, 4, 9, 16, 25
```

## 맵

키가 있는 데이터를 저장한다는 점에서 객체와 유사하지만, 키에 다양한 자료형을 허용한다.

- `new Map()` : 맵을 만든다.
- `map.set(key, value)` : `key` 를 이용해 `value` 를 저장한다.
- `map.get(key)` : `key` 에 해당하는 값을 반환한다. 없으면 undefined를 반환한다.
- `map.has(key)` : key가 존재하면 true, 아니면 false를 반환한다.
- `map.delete(key)` : key에 해당하는 값을 삭제한다.
- `map.clear()` : 맵 안의 모든 요소를 제거한다.
- `map.size` : 요소의 개수를 반환한다.

```jsx
let map = new Map();

map.set(1, 123);
map.set('1', '123123');
map.set(true, 'dfsaafsd');

console.log(map.get('1')); // '123123'
console.log(map.size); // 3
```

### 맵의 요소에 반복 작업

- `map.keys()` 각 요소의 키를 모은 반복 가능한 객체를 반환한다.
- `map.values()` 각 요소의 값을 모은 이터러블 객체를 반환한다.
- `map.entries()` 요소의 [키,값] 을 한 쌍으로 하는 이터러블 객체를 반환한다. 이 이터러블 객체는 `for...of` 반복문의 기초로 쓰인다.

```jsx
let recipeMap = new Map([
	['cucumber', 500],
	['tomatoes', 350],
	['onion', 50]
]);

for (let vegetable of recipeMap.keys()) console.log(vegetable);
for (let amount of recipeMaps.values()) console.log(amount);
for (let entry of recipeMaps) console.log(entry);
```

배열과 유사하게 내장 메서드 `forEach` 도 지원한다.

```jsx
recipeMap.forEach( (value, key, map) => {
	console.log(`${key} : ${value}`);
});
```

### 객체를 map으로, map을 객체로

객체를 맵으로 바꿀 때는 내장 메서드인 `Object.entries(obj)` 를 사용한다.

```jsx
let obj = {
	name: "John",
	age: 30;
};

let map = new Map(Object.entries(obj));
console.log( map.get('name') ); // John
```

그리고 map을 객체로 만들 때에는 내장 메서드인 `Object.fromEntries()` 를 사용한다.

```jsx
let prices = new Map();
prices.set('banana', 1);
prices.set('orange', 2);
prices.set('meat', 4);

obj = Object.fromEntries(prices);

console.log(obj);
```

## 셋

중복을 허용하지 않는 값을 모아 노은 컬렉션이다. 키가 없는 값이 저장된다.

- `new Set(iterable)` : 셋을 만든다. 이터러블 객체를 전달받으면 그 안의 값을 복사해 셋에 넣으준다.
- `set.add(value)` : 값을 추가하고 셋 자신을 반환한다.
- `set.delete(value)`  : 값을 제거한다. 제거에 성공하면 true, 아니면 false를 반환한다.
- `set.has(value)` : value가 있으면 true, 아니면 false
- `set.clear()` : 셋을 비운다.
- `set.size` : 셋의 값을 반환한다.

```jsx
let set = new Set();
let john = { name: "John" };
let pete = { name: "Pete" };
let mary = { name: "Mary" };

set.add(john);
set.add(pete);
set.add(john); // add 안 됨
set.add(pete); // add 안 됨
set.add(mary);

console.log(set.size);
```

### 셋에 반복 작업하기

`for...of` 나 `forEach` 를 이용하면 셋의 값을 대상으로 반복 작업을 수행할 수 있다.

```jsx
let set = new Set(["oranges", "apples", "bananas"]);
for (let value of set) console.log(`I like ${value}`);

set.forEach(value, valueAgain, set) => console.log(value);
// value와 valueAgain인 이유는 map과의 호환성 때문.
```

## 구조 분해 할당

할당 연산자 우측에는 어떠한 이터러블이든 올 수 있고, 좌측에는 어떠한 할당 가능한 값이든 올 수 있다.

### 배열, 문자열, 객체 분해하기

- 배열 분해하기
    
    ```jsx
    let arr = ['Yegang', 'Hwang'];
    let [name, givenName] = arr;
    console.log(name);
    console.log(givenName);
    ```
    
- 문자열 분해하기
    
    ```jsx
    let str = "Yegang Hwang";
    let [name, givenName] = str;
    ```
    
- 쉼표 사용하여 요소 무시하기
    
    ```jsx
    let str = ["Julius", "Caesar", "Consul", "of the Roman"];
    let [firstname, , title] = str;
    console.log(firstname + title);
    ```
    
- `.entries()` 로 반복하기 (맵에서도 가능)
    
    ```jsx
    let user = { name: "John", age: 30 };
    for (let [key, value] of Object.entries(user)) {
    	console.log(`${key}:${value}`);
    }
    
    let user2 = new Map();
    user2.set("name", "Donald");
    user2.set("age", 32);
    for (let [key, value] of user2) console.log(`${key}:${value}`);
    ```
    
- `...` 로 나머지 요소 가져오기
    
    ```jsx
    let [name1, name2, ...rest] = ["Julius", "Casaer", "Consul", "of the Roman"];
    
    console.log(name1); // "Julius"
    console.log(name2); // "Casaer"
    
    // rest는 배열임
    console.log(rest[0]); // Consul
    console.log(rest[1]); // of the Roman
    console.log(rest.length); // 2
    ```
    
- 객체 분해하기
    
    ```jsx
    let options = {
    	title: "Menu",
    	width: 100;
    	height: 200
    };
    
    let {height, width, title} = options; // 이렇게 해도 됨
    console.log(`${title} : ${width} : ${height}`);
    
    // {객체 프로퍼티 : 목표 변수}
    let {width:w, height:h, title:t} = options;
    console.log(`${w} ${h} ${t}`);
    ```
    
    - 나머지 패턴으로 객체 분해하기
        
        ```jsx
        let {title, ...rest} = options;
        console.log(rest.width);
        console.log(rest.height);
        ```
        
    

### 중첩 구조 분해

객체나 배열이 다른 객체나 배열을 포함하는 경우, 중첩 배열이나 객체의 정보를 추출할 수 있다. 이를 중첩 구조 분해라고 한다.

```jsx
let options = {
	size: {
		width: 100,
		height: 200
	},
	items: ["Cake", "Donut"],
	extra: true
};

let {
	size: {
		width,
		height
	},
	items: [item1, item2],
	title = "Menu" // options에 title 없으므로 기본값을 Menu
} = options;

console.log(title); // Menu
console.log(width); // 100
console.log(height); // 200
console.log(item1); // Cake
console.log(item2); // Donut
```

## Date 객체와 날짜

`Date` 객체를 이용하여 날짜/시간을 저장할 수 있고, 관련된 메소드도 사용이 가능하다.

`new Date()` 를 호출하면 새로운 `Date` 객체가 만들어지는데, 다음과 같이 호출이 가능하다.

1. `new Date()` : 현재 날짜와 시간이 지정된 Date 객체가 반환된다.
2. `new Date(milliseconds)` : 유닉스 시간을 밀리초 단위로 저장된 Date 객체를 반환한다.
3. `new Date(dateString)` : 문자열이라면 해당 문자열을 자동으로 구문 분석한다.
4. `new Date(year, month, date, hours, minutes, seconds, ms)`
    - `year` 는 반드시 네 자리 수여야 한다.
    - `month` 는 **0(1월) 부터 11(12월)** 까지이다.
    - `date` 는 날짜이며, 기본값은 1이다.
    - `hours`, `minuts`, `seconds`, `ms` 는 기본값이 0이다.
    
- 날짜 구성요소 얻기
    - `getFullYear()` : 4자릿수 연도를 반환
    - `getMonth()` : 월을 반환 **(0 이상 11 이하)**
    - `getDate()` : 일을 반환 **(0 이상 31 이하)**
    - `getDay()` : 요일을 반환 **(0 이상 6 이하). 0:일요일, 6:토요일**
    - `getHours()`, `getMinutes()` , `getSeconds()`, `getMilliseconds()`
    - `getTime()` : 주어진 일시와 유닉스 시간(밀리초 단위)인 타임스탬프를 반환
    - `getTimezoneOffset()` : 현지 시간과 표준 시간의 차이를 반환 (분단위)
- 날짜 구성요소 설정하기
    
    setFullYear, setMonth, setDate, setHours, setMinutes, setSeconds, setMilliseconds, setTime
    
    - 시간 더하기
        
        ```jsx
        let date = new Date();
        date.setHours( date.getHours() + 1 ); // 현재 시각에서 1시간 더함
        date.setDate( date.getDate() + 1 ); // 현재 날짜에서 1일 더함
        
        date = new Date("2025-12-31 23:59:59:999"); // 문자열 자동 구분
        date.setHours( date.getHours() + 1 );
        
        // 자동으로 올림 처리
        console.log(date.getFullYears()); // 2026
        console.log(date.getMonth()); // 0
        console.log(date.getDate()); // 1
        ```
        
- `Date.parse(str)` 문자열을 timestamp로 변환하는 함수
    
    문자열에서 날짜를 읽어올 수 있다. 단, 문자열의 형식은 `YYYY-MM-DDTHH:mm:ss:sssZ` 처럼 생겨야 한다.
    
    - `YYYY-MM-DD` : 년-월-일
    - `T` : 구분 기호로 좌측은 날짜, 우측은 시각
    - `HH:mm:ss.sss` : 시:분:초:밀리초
    - `Z` (옵션) :  `+-hh:mm` 형식의 국가별 시간대. Z 한 글자의 경우 UTC

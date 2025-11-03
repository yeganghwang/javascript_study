## 클래스
동일한 객체를 여러 개 생성할 때 사용할 수 있으며, 변수와 메서드를 정의한다.

### 기본 문법
클래스는 다음과 같은 기본 문법을 사용해 만들 수 있다.

```jsx
class MyClass {
	constructor() {...}
	method1() {...}
	method2() {...}
}
```

이렇게 클래스를 만들고, `new MyClass()`를 호출하면 내부에서 정의한 메서드가 들어 있는 객체가 생성된다. 객체의 기본 상태를 설정해주는 `constructor()`는 `new` 메서드에 의해 자동적으로 호출된다.

예시

```jsx
class User {
	constructor(name) {
		this.name = name;
	}
	
	sayHi() {
		console.log(`Hi, ${this.name}!`);
	}
}

// 사용법:
let user1 = new User("John");
let user2 = new User("Yegang");

user1.sayHi(); // Hi, John!
user2.sayHi(); // Hi, Yegang!
```

### 클래스 표현식
함수처럼 클래스도 다른 표현식 내부에서 정의, 전달, 반환, 할당할 수 있다.

```jsx
let User = class {
	sayHi() {
		console.log("안녕하세요");
	}
};
```

또는 기명 함수 표현식과 유사하게 클래스 표현식에도 이름을 붙일 수 있다.

이름을 붙이면 이 이름은 오직 클래스 내부에서만 사용할 수 있다.

```jsx
let User = class MyClass {
	sayHi() {
		console.log(MyClass); // MyClass라는 이름은 오직 클래스 내부에서만 사용 가능
	}
};

new User().sayHi();
console.log(MyClass); // MyClass is not defined
```

필요에 따라 클래스를 동적으로 생성하는 것도 가능하다.

```jsx
function makeClass(phrase) {
  // 클래스를 선언하고 이를 반환함
  return class {
    sayHi() {
      alert(phrase);
    };
  };
}

// 새로운 클래스를 만듦
let User = makeClass("안녕하세요.");

new User().sayHi(); // 안녕하세요.
```

### Getter / Setter
`get`과 `set`을 이용해 `user.name`을 조작할 수 있다.

getter와 setter는 문법 설탕으로, `get [멤버이름]`, `set [멤버이름]` 으로 사용한다. 실제로 저장되는 변수는 `name`이 아닌 `_name` 이다. getter/setter는 `name`으로 공개하고 실제 저장은 `_name`과 같은 private 변수 이름 규칙을 사용한다. 

```jsx
class User {
	constructor(name) {
		this.name = name; // set name(value)가 호출됨.
	}
	
	get name() {
		return this._name; // 실제로 반환되는 값은 _name임.
	}
	
	set name(value) {
		if (value.length < 4) {
			console.log("이름이 너무 짧습니다.");
			return;
		}
		this._name = value; // 실제로 저장되는 곳은 _name임.
	}
}

let user = new User("홍길동"); // 이름이 너무 짧습니다. (set name(value) 동작됨)
console.log(user.name); // undefined (getter 사용됨)

let user2 = new User("Yegang");
console.log(user2.name); // Yegang
```

### 계산된 메서드 이름 `[...]`
대괄호 `[...]`을 사용해 계산된 메서드 이름(Computed Method Name)을 만드는 것이 가능하다. 리터럴 객체와 유사하다.

```jsx
class User {
	['say' + 'Hi'] () {
		console.log("hello there!");
	}
} 

let user = new User();
user.sayHi(); // hello there!
```

### 클래스 필드
클래스 필드를 사용하면 어떤 종류의 프로퍼티도 클래스에 추가할 수 있다.

```javascript
class User {
	name = "Yegang";
	sayHi() {
		console.log(`${this.name}님 안녕하세요!`);
	}
}

new User().sayHi(); // Yegang님 안녕하세요!
```

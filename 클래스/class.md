## 클래스
동일한 객체를 여러 개 생성할 때 사용할 수 있으며, 변수와 메서드를 정의한다.

### 기본 문법
클래스는 다음과 같은 기본 문법을 사용해 만들 수 있다.

```javascript
class MyClass {
	constructor() {...}
	method1() {...}
	method2() {...}
}
```

이렇게 클래스를 만들고, `new MyClass()`를 호출하면 내부에서 정의한 메서드가 들어 있는 객체가 생성된다. 객체의 기본 상태를 설정해주는 `constructor()`는 `new` 메서드에 의해 자동적으로 호출된다.

예시
```javascript
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


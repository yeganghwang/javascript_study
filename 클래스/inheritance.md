### `extends` 키워드

클래스 상속을 이용하면 클래스를 다른 클래스로 확장할 수 있다. 기존에 존재하는 기능을 토대로 다른 기능을 만들 수 있다.

```jsx
class Animal {
	constructor(name) {
		this.speed = 0;
		this.name = name;
	}
	run(speed) {
		this.speed = speed;
		console.log(`${this.name}은/는 속도 ${this.speed}로 달립니다.`);
	}
	stop() {
		this.speed = 0;
		console.log(`${this.name}이/가 멈췄습니다.`);
	}
}

let animal = new Animal("동물");
console.log(animal); // {speed:0, name:"동물"}
animal.run(3); // "동물은/는 속도 3로 달립니다."
animal.stop(); // "동물이/가 멈췄습니다."
```

위 클래스 `Animal`을 확장하는 `Rabbit`을 만든다.

```jsx
class Rabbit extends Animal {
	hide() {
		console.log(`${this.name}이/가 숨었습니다!`);
	}
}

let rabbit = new Rabbit("흰 토끼");

rabbit.run(5); // 흰 토끼은/는 속도 5로 달립니다.
rabbit.hide(); // 흰 토끼이/가 숨었습니다!
```

클래스 `Rabbit`을 이용해 만든 객체는 `rabbit.hide()`와 같은 Rabbit에 정의된 메서드에도 접근할 수 있고, `rabbit.run()`같은 Animal에 정의된 메서드에도 접근할 수 있다. 

- 자세히
    
    키워드 `extends`는 프로토타입을 기반으로 동작한다. `extends`는 `Rabbit.prototype.[[Prototype]]` 을 `Animal.prototype`으로 설정한다. 그렇기 때문에 `Rabbit.prototype`에서 메서드를 찾지 못하면 `Animal.prototype`에서 메서드를 가져온다.
    

### 메서드 오버라이딩

클래스 `Rabbit`은 클래스 `Animal`에 있는 모든 메서드를 그대로 상속받는다. 그러나 `Rabbit`에서 `stop()` 등의 메서드를 자체적으로 정의하면 상속받은 메서드가 아닌 자체 메서드를 사용한다.

```jsx
class Rabbit extends Animal {
	hide() {
		console.log(`${this.name}이/가 숨었습니다!`);
	}
	stop() { // Animal의 stop()이 아닌 이 메서드가 사용된다.
		super.stop(); // 부모 클래스의 stop()을 호출하기 위해서는 super 키워드를 사용한다.
		this.hide();
	}
}
```

- `super.method(...)`는 부모 클래스에 정의된 메서드, `method`를 호출한다.
- `super(...)`는 부모 생성자를 호출하는데, 자식 생성자 내부에서만 사용할 수 있다.
- 화살표 함수에는 `super`를 지원하지 않는다.

### 생성자 오버라이딩

아래 코드는 오류가 발생한다.

```jsx
class Animal {
	constructor(name) {
		this.speed = 0;
		this.name = name;
	}
	run(speed) { this.speed = speed; // ... }
	stop() { this.speed = 0; // ... }
}

class Rabbit extends Animal {
	constructor(name, earLength) { // 이 부분
		this.speed = 0;
		this.name = name;
		this.earLength = earLength;
	}
}

let rabbit = new Rabbit("흰 토끼", 10); // 오류!
```

상송 클래스의 생성자에서는 반드시 `super(...)`를 호출해야 하는데, 호출하지 않아 에러가 발생했다. 반드시 `this`를 사용하기 전에 호출해야 한다.

- 자세히
    
    자바스크립트는 상속 클래스의 생성자 함수와 일반 생성자 함수를 구분한다. 일반 클래스의 생성자 함수와 상속 클래스의 생성자 함수 간 차이는 `new`와 함께 드러난다.
    
    - 일반 클래스가 `new`와 함께 실행되면 빈 객체가 만들어지고 `this`에 이 객체를 할당한다.
    - 반면 상속 클래스의 생성자 함수가 실행되면, 상속 클래스의 생성자 함수는 빈 객체를 만들고 `this`에 이 객체를 할당하지 않는다.
    
    이런 차이 때문에 상속 클래스의 생성자에서는 `super`를 호출해 부모 생성자를 실행해 주어야 한다. 그렇지 않으면 `this` 가 될 객체가 만들어지지 않아 에러가 발생한다.
    

```jsx
class Animal {
	constructor(name) {
		this.speed = 0;
		this.name = name;
	}
	// ... run, stop 등
}

class Rabbit extends Animal {
	constructor(name, earLength) {
		super(name); // super 지정
		this.earLength = earLength;
	}
	// ... hide 등
}

// 잘 동작!
let rabbit = new Rabbit("흰 토끼", 10);
console.log(rabbit.name); // 흰 토끼
console.log(rabbit.earLength); // 10
```

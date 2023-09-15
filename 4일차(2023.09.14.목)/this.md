> [!tip]
> JavaScript에서 **함수의 `this` 키워드**는 다른 언어와 조금 다르게 동작합니다. 
> 또한 엄격 모드와 비엄격 모드에서도 일부 차이가 있습니다.
> 대부분의 경우 `this`의 값은 함수를 ⭐️호출한 방법⭐️에 의해 결정됩니다. 
> 실행중에는 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있습니다. ES5는
>  함수를 어떻게 호출했는지 상관하지 않고
>  `this` 값을 설정할 수 있는 `bind` 메서드를 도입했고, 
>  ES2015는 스스로의 `this` 바인딩을 제공하지 않는 [[화살표함수]]를 추가했습니다.

- `this`는 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(self-reference variable)이다.
- 전역 실행 맥락에서 `this`는 엄격 모드 여부에 관계 없이 전역 객체를 참조.
- 함수 내부에서 `this`의 값은 함수를 ⭐️호출한 방법⭐️에 의해 좌우된다.
	1. 함수 호출
	2. 메서드 호출
	3. 생성자함수 호출
	4. [[apply]], [[call]], [[bind]] 통해서 호출
	 ```javascript
	foo(); // this -> window
	
	// 2. 메소드 호출
	var obj = { foo: foo };
	obj.foo(); // this -> obj
	
	// 3. 생성자 함수 호출
	var instance = new foo(); // instance
	
	// 4. apply/call/bind 호출
	var bar = { name: 'bar' };
	foo.call(bar);   // bar
	foo.apply(bar);  // bar
	const boundFunc = foo.bind(bar);
	```
- 객체의 메서드로 실행할 경우, 객체가 `this`에 할당된다.
- `this`의 값을 상정하여 실행한다면 [[call]]이나 [[apply]]를 사용.
- `this`의 값을 정하여 새로운 함수를 리턴한다면 [[bind]]를 사용.
- 프로토타입 체이닝을 통해서 `this` 값 binding!
- 생성자 함수를 통해 호출될 경우 `this`값은 생성된 객체.
- 콜백 함수를 통해 호출된 경우 함수는 복사되었기 때문에, `this`값은 `window`일 경우가 많다. [[call]], [[apply]], [[bind]]로 `this` binding 가능
#### 생성자함수와 함께하는 `this`
- 함수를 [[new]] 키워드와 함께 생성자로 사용하면 `this`는 새로 생긴 객체(인스턴스)에 묶입니다.

#### DOM과 함께하는 `this`
- 함수를 이벤트 처리기로 사용하면 this는 이벤트를 발사한 요소로 설정됩니다.
```javascript
function bluify(e) {
  // 언제나 true
  console.log(this === e.currentTarget);
  // currentTarget과 target이 같은 객체면 true
  console.log(this === e.target);
  this.style.backgroundColor = "#A5D9F3";
}

// 문서 내 모든 요소의 목록
var elements = document.getElementsByTagName("*");

// 어떤 요소를 클릭하면 파랗게 변하도록
// bluify를 클릭 처리기로 등록
for (var i = 0; i < elements.length; i++) {
  elements[i].addEventListener("click", bluify, false);
}
```
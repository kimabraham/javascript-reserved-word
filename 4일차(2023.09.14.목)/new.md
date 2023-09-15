> [!tip]
> **`new` 연산자**는 사용자 정의 객체 타입 또는 내장 객체 타입의 *인스턴스를 생성*한다.

```javascript
// 구문
new constructor[([arguments])];

// 예제
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

const car1 = new Car('Eagle', 'Talon TSi', 1993);

console.log(car1.make);
// Expected output: "Eagle"
```

1. `constructor` : 객체의 인스턴스 타입을 기술하는 함수!
2.  `arguments` : [옵션] constructor와 함께 호출될 값(목록);

### 객체를 생성하는 두 단계
1. 함수를 작성한다. 객체의 속성을 기술한다.
2. `new`연산자를 이용하여 생성자 함수에서 부터 인스턴스 객체를 만든다.

예시) `new Foo(...)`

1. `Foo.prototype` 을 상속하는 새로운 객체가 하나 생성된다.
 ![[스크린샷 2023-09-14 오후 4.06.13.png]]
2. 명시된 인자 그리고 새롭게 생성된 객체에 바인드된 [[this]]와 함께 
   생성자 함수 `Foo`가 호출된다.
   `new Foo`는 `new Foo()`와 동일하다. 
   즉 인자가 명시되지 않은 경우, 인자 없이 `Foo`가 호출된다.
3. 생성자 함수에 의해 리턴된 객체는 전체 `new` 호출 결과가 된다. 
   만약 생성자 함수가 명시적으로 객체를 리턴하지 않는 경우, 
   첫 번째 단계에서 생성된 객체가 대신 사용된다.
   (일반적으로 생성자는 값을 리턴하지 않는다. 그러나 일반적인 객체 생성을 재정의(override)하기 원한다면 그렇게 하도록 선택할 수 있다.)
   ![[Pasted image 20230914195216.png]]


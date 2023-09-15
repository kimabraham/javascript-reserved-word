> [!tip]
> **`instanceof` 연산자**는 생성자의 `prototype` 속성이 
> 객체의 프로토타입 체인 어딘가 존재하는지 판별합니다.

```javascript
// 구문
object instanceof constructor;

// 예제
function Car(make, model, year) {
  this.make = make;
  this.model = model;
  this.year = year;
}

const auto = new Car('Honda', 'Accord', 1998);

console.log(auto instanceof Car);
// Expected output: true

console.log(auto instanceof Object);
// Expected output: true

console.log(Car instanceof Object);
// Expected output: true
```

- `object`가 `constructor`의 인스턴스인지 여부!, 하지만 체인까지 고려하여 확인
- 대부분은 `Object`의 `instance`이다.
```javascript
[1,2,3,4,5] instanceof Array; // true
Array instanceof Object;      // true
[1,2,3,4,5] instanceof Object;// true
'string' instanceof Object;   // ⭐️ false
new String('string') instanceof Object; // true
```
- [[prototype]]에 대한 깊은 이해가 필요하다. mdn의 후반부가 이해되지 않는다.
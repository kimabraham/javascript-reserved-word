> [!tip]
> **`Object.defineProperty()`** 정적 메서드는 객체에 새로운 속성을 직접 정의하거나 
> 이미 존재하는 속성을 수정한 후, 해당 객체를 반환합니다.


```javascript
Object.defineProperty(obj, prop, descriptor);


// 예제
const object1 = {};

Object.defineProperty(object1, 'property1', {
  value: 42,
  writable: false,
});

object1.property1 = 77;
// Throws an error in strict mode

console.log(object1.property1);
// Expected output: 42

// 객체 보호 option configuration:false
Object.defineProperty(Employee, "name", { configurable: false });
```
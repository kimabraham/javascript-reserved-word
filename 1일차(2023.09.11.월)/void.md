>[!TIP]
> **`void` 연산자**는 주어진 표현식을 평가하고 `undefined`를 반환합니다.

- void 연산자는 값을 생성하는 표현식을 평가하여 `undefined` 를 반환한다.
- 주어진 식을 평가한다.
- return 값이 undefined이다.

```javascript
void 2=='2' // void 2 → undefined , undefined == '2' → false
// void 역시 연산자이기 때문에 괄호 연산자를 통해서 우선순위를 줄 수 있다.
void (2=='2') // 2=='2' → true → void true → undefined

void (function iife() {
  console.log('iife is executed');
})(); // 우선 함수를 실행한다. 그러나 iife함수는 undefined로 존재하지 않는다.

void function test() {
  console.log('test function executed');
}; // 함수를 평가하나, 실행되지는 않고, test함수 역시 undefined로 존재하지 않는다.

```

- `void` 가 연산자라는 개념을 인지해야 한다.
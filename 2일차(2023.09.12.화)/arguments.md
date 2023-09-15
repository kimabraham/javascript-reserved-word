> [!tip]
> `arguments` 객체는 모든 함수 내에서 이용 가능한 지역 변수입니다. 
> `arguments` 객체를 사용하여 함수 내에서 모든 인수를 참조할 수 있으며, 
> 호출할 때 제공한 인수 각각에 대한 항목을 갖고 있습니다. 항목의 인덱스는 0부터 시작합니다.

- 함수의 인자를 함수 내에서 지역적으로 사용하는 [[유사배열객체]]이다.
- 요즘은 많이 사용하지 않는 것으로 알고있다. 나머지 매개변수(스프레드) 사용. 이유는 위와 같이 유사배열 객체로서 배열 메서드로 관리하기 힘들기 때문이다.
```javascript
var args = Array.from(arguments);
var args = [...arguments];
var args = Array.prototype.slice.call(arguments);
var args = [].slice.call(arguments);
// 유사배열객체 → 배열 변환하는 방법들...
```

1. 나머지 매개변수
```javascript
function foo(...args) {
  console.log(...args); // Array [1,2,3]
  return arguments; // 유사배열 객체
}
foo(1, 2, 3); // { "0": 1, "1": 2, "2": 3 } 유사배열 객체
```

2. 기본값 매개변수
```javascript
function bar(a = 1) {
  arguments[0] = 100;
  return a;
}
bar(10); // 10 값이 없으면 1
```

3. 비구조화된 매개변수
```javascript
[a, b, ...rest] = [10, 20, 30, 40, 50];
```

- 비엄격 함수에서는 `arguments` 객체는 함수가 어떤 나머지 매개변수, 기본 매개변수 또는 비구조화된 매개변수 든 포함하지 않는 경우에만 제공됩니다.
- 
❓왜 그러는 건지... 
✅ 나머지 매개변수, 기본 매개변수, 비구조화된 매개변수 모두 `arguments`보다 늦게 나온 개념(기능)들이다. 아마 위 기능들을 사용할 경우 기존 `arguments`의 기능들을 사용하거나 하기 때문에 `arguments`의 기능을 제한하는 것으로 사료된다.
```javascript
function zoo(a) {
  arguments[0] = 100;
  return a;
}
zoo(10); // 100, 나머지 매개변수, 기본 매개변수, 비구조화된 매개변수를 사용하지 않았기에, arguments로서 정상 작동함.
```
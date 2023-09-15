> [!tip]
> **`let`** 명령문은 블록 스코프의 범위를 가지는 지역 변수를 선언하며, 선언과 동시에 임의의 값으로 초기화할 수도 있습니다.(선언과 동시의 임의의 값으로 초기화 하지 않을 수도 있다) 단, const는 임의의
> 

```javascript
let name1;
let name1 = value1;
let name1 = value1, name2 = value2;
let name1, name2 = value2;
let name1 = value1, name2, /* …, */ nameN = valueN;
```

- 블록 스코프 범위(바깥에서 안쪽으로는 접근 불가! 역방향은 가능, [[스코프 체인]])
```javascript
var a = 1;
var b = 2;

if (a === 1) {
  var a = 11; 
  // 전역 변수 var는 함수 범위 스코프이기 때문에 블록 스코프 안에서의 선언은 전역에서의 선언과 동일
  let b = 22; // if 블록 변수

  console.log(a); // 11
  console.log(b); // 22
}

console.log(a); // 11
console.log(b); // 2 let b가 출력되지 않고 var b가 출력된 이유 역시 let b는 블록 범위 스코프이기 때문에 바깥으로 나올 수가 없고, 그렇기 떄문에 가장 가까이에 있는 var b가 출력된다.
```

- [[TDZ]](Temporal Dead Zone)
```javascript
function do_something() {
  console.log(bar); // undefined
  console.log(foo); // ReferenceError
  // ** 만약 let이 호이스팅이 안된다면,
  // foo 가 정의되지 않았다는 에러가 발생하겠지만,
  // 실질적으로 같은 참조에러지만, initialize 하기전 접근할 수 없다는 에러를 발생시킨다.
  // 시간적인 사각지대(선언과 초기화가 별도다) 반면 var는 선언과 초기화가 동시에 이뤄진다.
  var bar = 1;
  let foo = 2;
}
```

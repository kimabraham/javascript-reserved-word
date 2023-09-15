[[변수란]]
```javascript
var name1;
var name1 = value1;
var name1 = value1, name2 = value2;
var name1, name2 = value2;
var name1 = value1, name2, /* …, */ nameN = valueN;

function x() {
  y = 1; // 'var' 선언 없이도 할당이 가능하다. 하지만, strict 모드에서는 ReferenceError를 출력
  var z = 2;
}
```

- `var` 는 함수 범위의 변수 할당자이다.
- 재선언이 가능하다. 또한 할당자 없이 선언 역시 가능(strict모드에서는 불가능)(또한 `let` or `const` 를 통해 선언된 변수명에 대해서는 재선언 불가능)
- [[Hoisting]]가능
- [[전역변수]] (선언되지 않은 변수 & 글로벌 환경에서의 선언시)의 속성으로 등록.

1. 선언된 변수들은 변수가 선언된 실행 콘텍스트(execution context) 안에서 만들어집니다. 선언되지 않은 변수들(`var` 없이 한 것들)은 항상 전역변수이다.❇️
```javascript
function x() {
  y = 1; // strict 모드에서는 ReferenceError를 출력합니다. 
  // 선언되지 않은 변수들은 항상 전역변수 이다. (1)
  var z = 2; // 선언된 변수는 실행 콘텍스트 안에서 만들어 진다. (2)
}

x();

console.log(y); // 로그에 "1" 출력합니다. 
// 그래서 (1) 은 전역변수 이므로 함수 바깥에서 접근 가능하다.
console.log(z); // ReferenceError: z is not defined outside x를 출력합니다.
// 하지만 (2)의 z는 함수의 실행컨텍스트 안에서만 있으므로 함수에서만 활용가능하다.
// var 는 함수 스코프이다.
```

2. 선언된 변수들은 어떠한 코드가 실행되기 전에 만들어집니다. 선언되지 않은 변수들은 변수들을 할당하는 코드가 실행되기 전까지는 존재하지 않습니다.
```javascript
console.log(a); // ReferenceError를 출력합니다.
// a는 선언되지 않은 변수이므로 어떠한 코드가 실행되기 전에 만들어 지지 않는다.
// undefined 도 아니기 때문에 참조에러가 발생한다.
console.log("still going..."); // 결코 실행되지 않습니다.
```

3. 선언된 변수들은 변수들의 실행 콘텍스트(execution context)의 프로퍼티를 변경되지 않습니다. 선언되지 않은 변수들은 변경 가능합니다. (e.g 삭제 될 수도 있습니다.)
```javascript
var a = 1; // 선언된 변수
b = 2; // 선언되지 않은 변수
// 위 변수들은 모두 window에 속성으로 저장된다.

delete this.a; // this → window false. a 는 살아있다.
// strict 모드에서는 TypeError를 출력합니다. 그렇지 않으면 자동적으로 실패합니다.
delete this.b; // b 는 삭제된다.
// var 를 이용하여 선언한 변수는 window 객체의 구성불가속성으로 추가된다. 삭제가 불가능 하다. 가비지 콜렉터로 삭제된다. 

console.log(a, b); // ReferenceError를 출력합니다.
// 'b' 프로퍼티는 삭제되었고, 어디에도 존재하지 않습니다.
```

### `var` 의 문제점
1. 예상할 수 없다.
	- 호이스팅과 함수 수준의 스코프는 언제 어디서 참조할 지, 예측할 수 없게 만드는 경우가 있다.
	- ex) for문에서의 i 값 (함수 수준이기 때문에 for 문 바깥에서도 변화된 값이 적용된다. 전역변수에 저장됬기 때문에)
	- 호이스팅과 함수 수준의 스코프기 떄문에 위의 가까운 변수가 아니라 밑에 있는 var의 값을 호이스팅하여 가져오는 경우가 생긴다.(예측할 수 없다.)
	- 역시 위와 같은 이유로 오류를 발생시키지 않는다.(변수 중복등 휴먼 에러를 캐치하기 힘들것으로 생각됨)
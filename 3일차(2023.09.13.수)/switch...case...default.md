>[!tip]
>`switch` 문은 일련의 `case` 절과 식의 값을 일치시켜 식을 평가하고
>(case 뒤는 상수값만 조건 불가)
> `case` 절 뒤에 있는 문장을 중단문(`break`)이 있을 때까지 실행합니다. 
>`switch` 문의 `default` 절은 식의 값과 일치하는 `case`가 없는 경우로 점프됩니다.
>`switch`문을 사용한 비교법은 특정 변수를 다양한 상황에서 비교할 수 있게 해줍니다.(*)

```javascript
const num = 2
switch (num){
	case num > 0 :    //변수와 비교 불가❌
		console.log( "입력한 숫자는 양수입니다." );
		break;
	case num = 0 :     //변수와 비교 불가❌
		console.log( "입력한 숫자는 0입니다." );
		break;
	case num < 0 :     //변수와 비교 불가❌
		console.log( "입력한 숫자는 음수입니다." );
		break;
	default
		console.log( "숫자를 입력해주세요." );
}
```

```javascript
let a = "1";
let b = 0;

switch (+a) {
	case b + 1: // 이렇게 다양한 형태로 
		console.log("표현식 +a는 1, 표현식 b+1는 1이므로 이 코드가 실행됩니다.");
		break;
	default:
		console.log("이 코드는 실행되지 않습니다.");
}
```

```javascript
switch (expression) {
  case value1:
    statements
    [break]
  case value2:
    statements
    [break]
  // …
  case valueN:
    statements
    [break]
  default:
    statements
    [break]
}
```

- `expression` 이 `case`의 다음의 `value`값과 일치할 경우 그에 해당하는 `statements`가 실행된다.
- 해당되는 `case`가 없을 경우 `default`에 해당하는 `statements`가 실행된다.
- switch...case... 문은 기능상 [[if...else...]]문과 서로 상호적으로 구현할 수는 있다.
- switch...case... 문을 사용할 때 유의❗️case 절에 `break`가 없는 경우 `default`까지 실행된다. 
- `break`가 옵션값이지만, `switch`로서의 기능을 잘 구현하기 위해서 `break`사용이 필수적으로 보인다. 혹은 함수 내에서 사용한다면 `return`사용도 가능하겠다.
```javascript
let a = 2 + 2;

switch (a) {
	case 3:
		console.log( '비교하려는 값보다 작습니다.' );
	case 4:
		console.log( '비교하려는 값과 일치합니다.' );
	case 5:
		console.log( '비교하려는 값보다 큽니다.' );
	default:
		console.log( "어떤 값인지 파악이 되지 않습니다." );
}
// 모든 console.log()가 실행된다.
```

```javascript
let a = 3;

switch (a) {
	case 4:
		console.log('계산이 맞습니다!');
		break;
	case 3: // (*) 두 case문을 묶음
	case 5:
		console.log('계산이 틀립니다!');
		console.log("수학 수업을 다시 들어보는걸 권유 드립니다.");
		break;
	default:
		console.log('계산 결과가 이상하네요.');
}
// 3일 때도 5일 때도 (*) 이하 문이 실행된다.
```
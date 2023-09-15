> [!tip]
> **`if` 문**은 지정한 조건이 참([[true]])인 경우 명령문(statement)을 실행합니다. 
>  조건이 거짓([[false]])인 경우 또 다른 명령문이 실행 될 수 있습니다.

```javascript
if (condition1)
   statement1
[else if(condtion2)
	statement3]     // 중첩가능
[else
   statement2]
```

- `condition1`
	1. 값이 [[참]]일 경우, `statement1`을 실행한다.
- `statement1`
	1. `condition`의 값이 [[참]]일 경우 실행된다.
	2. 다중 조건 구문일 경우 블록 문으로 구분한다.
- `statement2`
	1. `else if`구문이 존재하지 않는다는 조건하에, `condition`이 참인 경우가 아닐 경우에 실행된다.
- `statement3`
	1. `else if`구문이 존재할 경우 실행 되는 명령문으로, `condition2`의 값이 참일 경우 실행된다.
	2. 단⭐️, 코드가 위에서 부터 실행되므로 `condition1`에도 참이 된다면, `statement1`이 실행된다.
       3. ex)
  ```javascript
  const a = 10;
  if(a % 2 === 0){ 	  // a가 2의 배수입니까? (1)
	  console.log('a는 2의 배수 입니다.');
  }else if(a % 5 === 0){ // a가 5의 배수 입니까? (2)
	  console.log('a는 5의 배수 입니다.');
  }else{
	  console.log('a는 2의 배수도 아니고 5의 배수도 아닙니다.');
  }

  // a는 2의 배수 입니다.
  // a는 5의 배수임에도 불구하고 'a는 5의 배수 입니다.'라는 것이 실행하지 않았다.
  ```

#### if문 중첩사용
- 얼마든지 중첩가능하나, 가독성 및 논리적으로 사고하기 힘들다...
```javascript
if (조건1)
   명령문1
else
   if (조건2)
	  명령문2
   else
	  if (조건3)
...
```

❓할당문이 [[true]]라니,,,,
```javascript
let x = 1;
let y = 10;

Boolean(x=y); true

if( (x=y) ){
	console.log('true');
}

// true
```
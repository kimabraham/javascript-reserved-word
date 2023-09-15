> [!tip]
> **`for` 문**은 
> 1. 괄호로 감싸고 
> 2. 세미콜론으로 구분한 세 개의 선택식과, 
> 3. 반복을 수행할 문
> 4. (주로 블럭문)으로 이루어져 있습니다. ❓주로 블럭문이라는 것?

```javascript
// 1. 괄호로 감싸고
for(let i=0; i<9; i+=1){ // 2. 세미콜론으로 구분한 세 개의 선택식과
	console.log(i);      // 3. 반복을 수행할 문
}                        // 4. 주로블록문으로 이루어져 있습니다.
```
#### 구문
```javascript
for ([initialization]; [condition]; [final-expression])
   statement
```

- `initialization`
	1. 변수를 초기화
	2. `var` or `let` 을 통해서 새로운 변수를 선언 가능. 
	3. `let` 키워드로 선언한 변수는 반복문의 지역 변수가 됩니다.
	   (`var`로 선언하거나 외부 변수를 초기값으로 가져온 반복문에서는 아니다.)
 ```javascript
 // 1. 반복문이 시작될 때 변수를 초기화 한다. var 또는 let으로 가능하다.
 for(let i = 1; i < 10; i++){
	 console.log(i) // 1~10
 }
 console.log(i) // ReferenceError: i is not defined
 // 2. 그러나 var를 통한 변수 선언은 외부에서 접근이 가능하다. 아래 2개의 예제는 결과가 같다.
 for(var i = 1; i < 10; i++){
	 console.log(i) // 1~10
 }
 console.log(i) // 10
 
 let i = 1;
 for(; i < 10; i++){
	 console.log(i) // 1~10
 }
 console.log(i) // 10

// 추가 final-expression(step)역시 옵션이다.
for(let i=0; i<10;){ // step 사용 안할 경우 마지막 세미콜론 불필요!
	console.log(i);
	i++;
}
 ```
- `condition`
	1. `true` 일 경우 for문에 해당되는 블럭의 문([[statement]])들을 실행한다.
- `final-expression`
	1. 당연히 `condition`전에 발생한다.(`condition`이 `true`면 `statement`실행하고, `final-expression`하고, 다시 `condition`으로 간다.)
	2. `condition`→`true`→`statement`→`final-expression`→`condition` ... [[continue]]
	3. `condition`→`false`→`for`문에서 빠져나온다. [[break]]
	```javascript
	for (var i = 0; ; i++) {
	  console.log(i);
	  if (i > 3) break;
	  // 기타 등등
	}
	```
	
#### 또 다른 반복문
1. [[for ... of ...]]
2. [[for ... in ...]]
3.  `forEach`, `map`, `reduce` 등 배열함수들에 대한 정리는 다른 챕터에서 진행.

#### 기타 개념
1. [[break]]
2. [[continue]]
3. [[label]]
4. [[증감연산자]](전위형, 후위형)
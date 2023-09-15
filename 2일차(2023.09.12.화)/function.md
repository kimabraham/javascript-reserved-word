> [!tip]
> 함수란 어떤 작업을 수행하기 위해 필요한 문(statement)들의 집합을 정의한 코드 블록이다. 
> 함수는 이름과 매개변수를 갖으며 필요한 때에 호출하여 코드 블록에 담긴 문들을 일괄적으로 실행할 수 있다.

- 함수의 정의
	1. 함수 선언식(함수 호이스팅:선언되기 전에 호출 가능)
	```javascript
	function square(number) { 
		return number * number; 
	}
	```

	2. 함수 표현식(함수는 [[일급객체]]이다.)(변수 호이스팅:변수와 같은 형식으로 호이스팅, `undefined`)
	 ```javascript
	// 기명 함수 표현식(named function expression)
	var foo = function multiply(a, b) { 
		return a * b; 
	};
	// 익명 함수 표현식(anonymous function expression) 
	var bar = function(a, b) { 
		return a * b; 
	};
```

	3. Function 생성자 함수(함수를 생성하는 함수) [[생성자 함수]]
		- 함수 표현식은 함수 리터럴 방식을 통하여 함수를 정의한다.
		- 함수 선언식 역시 최적화 과정을 거치면서 결국 함수 표현식으로 변환되고, 함수 리터럴 방식을 통하여 정의되는 것이다.
		- 함수 역시 객체이다. 함수 리터럴을 통해서 함수를 생성할 수 있다.
	 ```javascript
	 new Function ([arg1[, arg2[, ...argN]],] functionBody)
	 // ex
	 const sum = new Function('a', 'b', 'return a + b');
	```

- 매개변수로 인자가 들어올 때, 복사되어 들어온다. 변경시 일반 변수로 복사하는 것과 마찬가지로, 변경시 원시값은 기존 변수가 그대로이고, 참조값은 같이 바뀐다.
#### 함수는 [[일급객체]]이다.

## 함수의 다양한 형태

1. [[즉시실행함수]]
2. [[내부함수]]
3. [[재귀함수]]
4. [[콜백함수]]
5. [[화살표함수]]

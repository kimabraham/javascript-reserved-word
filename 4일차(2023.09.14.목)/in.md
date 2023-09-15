> [!tip]
> **`in` 연산자**는 명시된 속성이 명시된 객체에 존재하면 `true`를 반환합니다.

- 객체(obj객체, arr객체, 유사배열객체 등)에서 사용할 수 있다.
```javascript
// ⭐️ 배열에서 in을 사용할 때에는, index를 의미한다.

var trees = new Array("redwood", "bay", "cedar", "oak", "maple");
0 in trees; // true를 반환합니다. 
3 in trees(1 + 2) in trees;
↓
3 in trees, 3 in trees;
// true를 반환합니다. 연산자 우선 순위에 의하여 이 구문의 괄호는 없어도 됩니다.
6 in trees; // false를 반환합니다.

⭐️ "bay" in trees; 
// false를 반환합니다. 당신은 배열의 내용이 아닌, 인덱스 값을 명시하여야 합니다.
"length" in trees; 
⭐️⭐️ // true를 반환합니다. length는 Array(배열) 객체의 속성입니다.

// 미리 정의된 객체 // 빌트인객체
"PI" in Math; // true를 반환합니다.
"P" + "I" in Math; // true를 반환합니다.

// 사용자가 정의한 객체
var myCar = {
  company: "Lamborghini",
  model: "Lamborghini Veneno Roadster",
  year: 2014,
};
"company" in myCar; // true를 반환합니다.
"model" in myCar; // true를 반환합니다.

// 유사배열객체
var color1 = new String("green");
"length" in color1; // true를 반환합니다.

var color2 = "coral";
"length" in color2; // color2는 String 객체가 아니기에 오류를 냅니다.
```
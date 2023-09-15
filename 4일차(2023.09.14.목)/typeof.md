> [!tip]
> **`typeof`** 연산자는 피연산자의 평가 전 자료형을 나타내는 ⭐️문자열⭐️을 반환합니다.

```javascript
typeof operand;
typeof (operand);

console.log(typeof 42);
// Expected output: "number"

console.log(typeof 'blubber');
// Expected output: "string"

console.log(typeof true);
// Expected output: "boolean"

console.log(typeof undeclaredVariable);
// Expected output: "undefined"

```

![[스크린샷 2023-09-14 오후 3.23.42.png]]

- ⭐️ `null` → `object` ⭐️
- 예상하지 못했던 `type`
```javascript
typeof class C {} === "function";
typeof new Date() === "object";
typeof new Boolean(true) === "object";
typeof new Number(1) === "object";
typeof new String("abc") === "object";
```

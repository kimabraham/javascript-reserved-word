> [!tip]
> **`return` 명령문**은 함수 실행을 종료하고, 주어진 값을 함수 호출 지점으로 반환합니다.

```javascript
return expression;
```
- `return`을 만날 경우 해당 함수를 종료한다. 그리고 호출 시점으로 이동한다.
- 표현식을 생략할 경우, `undefined` 를 반환한다.
- `return`이 없는 함수는 자동으로 `undefined`를 반환한다.⭐️

#### 자동 세미콜론
- `return` 키워드와 표현식 사이에는 줄바꿈 문자가 올 수 없다.
```javascript
return
a + b
// ↓
return;
a + b;
// 주의 만약 이렇게 가독성이나 기타 이유로 위와 같이 표현하고자 한다면
return (
  a + b
);
```

❓ 스코프를 벗어나고, 만약 함수의 호출에 의한 것이라면 호출된 장소로 이동하는 것?, 그런데 window 에서 `return`만 실행 하면 `Uncaught SyntaxError: Illegal return statement` 에러 발생, node에서는 정상! 실행 차이점?
✅ 결과를 보면 node 환경은 글로벌 함수라고 보여지고, window환경은 전역 scope로 보는걸로... 결과를 보고 원인을 유추!
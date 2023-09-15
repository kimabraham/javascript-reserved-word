> [!tip]
> The **`try...catch`** statement is comprised of a `try` block and either a `catch` block, a `finally` block, or both. The code in the `try` block is executed first, and if it throws an exception, the code in the `catch` block will be executed. The code in the `finally` block will always be executed before control flow exits the entire construct.

```javascript
// Syntax
try {
  tryStatements
} catch (exceptionVar) {
  catchStatements
} finally {
  finallyStatements
}
```

- `tryStatements` : 무조건 실행된다.
- `catchStatements` : `tryStatements`에서 예외 사항이 발생되면 실행된다.
- `finallyStatements` : 전체 구문이 끝나기 전에 예외사항 발생과 무관하게 항상 실행된다. 
- `try...catch...`문을 사용하면 코드가 에러로 인하여 죽는 것을 방지한다.

#### 사용방법
- `try...catch`
- `try...finally`
- `try...catch...finally`
- `try` 혼자 단독 사용 불가
#### `try..catch`는 오직 런타임 에러에만 동작합니다.
- 컴파일 오류 : 문법오류
- 런타임 오류 : 논리오류
 ![[스크린샷 2023-09-15 오후 2.46.03.png]]![[스크린샷 2023-09-15 오후 2.46.07.png]]

#### `try..catch`는 동기적으로 동작합니다.
```javascript
try {
  setTimeout(function() {
    noSuchVariable; // 스크립트는 여기서 죽습니다.
  }, 1000);
} catch (e) {
  alert( "작동 멈춤" );
}
```

### error ([[throw]]를 통하여 실행 가능)
`name`
에러 이름. 

`message`
에러 상세 내용을 담고 있는 문자 메시지
`name`과 `message` 이외에 대부분의 호스트 환경에서 지원하는 프로퍼티도 있다. 
`stack`은 가장 널리 사용되는 비표준 프로퍼티 중 하나입니다.

`stack`
현재 호출 스택. 에러를 유발한 중첩 호출들의 순서 정보를 가진 문자열로 디버깅 목적으로 사용.

#### finally
- return, break, continue 등 코드의 실행 흐름이 즉시 이동되더라도 무조건 실행된다.
- 에러가 안 났을 때: try - finally
- 에러가 났을 때: try - 에러발생 - catch - finally
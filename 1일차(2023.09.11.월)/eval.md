>[!IMPORTANT]
> `eval` 을 쓰는 것은 굉장히 위험하다. `eval` 사용을 통해서 해커가 코드를 사용할 수 있다.

```javascript
eval(string);
```

- `eval`의 인자인 문자열을 `javascript`코드처럼 사용할 수 있다.
- 주어진 코드를 평가하여 얻은 값. 값이 없다면 `undefined`를 반환한다.
### eval 이 보안에 취약한 이유
[eval is evil](https://logical-code.tistory.com/102)
1. 전역변수를 변경할 가능성이 있다. 왜냐면 최적화를 안하고 바로 실행하기 때문에,
2. 유튜브에서 들었던 기억이 난다. `eval`을 이용하여 `query`를 실행시켜 DB를 날려버린다.
3. 또한 eval 자체가 최적화가 안되기 때문에 굉장히 느려서 굳이 쓸 필요가 없다.

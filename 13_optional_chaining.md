# 옵셔널 체이닝 `'?.'`(Optional Chaining)

프로퍼티가 없는 중첩 객체에 에러 없이 안전하게 접근 가능

> 참조나 기능이 undefined 또는 null일 수 있을 때 연결된 객체의 값에 접근하는 단순화할 수 있는 방법을 제공한다 - [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Optional_chaining)

## 문법

**`obj?.prop`**

**`obj?.[prop]`**

**`obj?.method()`**

: obj가 존재하면 `obj.prop`(또는 `obj?.[prop]` 또는 `obj?.method()`)을 반환하고,  그렇지 않으면 undefined를 반환

`?.` `왼쪽` 평가대상이 null 혹은 undefined인지 확인 후, 아니라면 평가를 계속 진행

## 단락평가(short-circuit)

`?.` 왼쪽 평가대상에 값이 없으면 즉시 평가를 멈춤

```javascript
let user = null;
let a = 0;

user?.sayHello(x++); // user가 null이므로 아무 일도 일어나지 않음
console.log(x); // 0 , 원래 값 그대로. 값이 증가하지 않음
```

### 주의할 점

- `?.`왼쪽 평가대상이 존재하지 않아도 괜찮은 경우에만 선택적으로 사용해야 함

    반드시 있어야 하는 필수값인데 값을 할당하지 않았다면 추후 디버깅이 어려워짐

- `?.`앞의 변수는 꼭 선언되어 있어야 함

# 객체를 원시형으로 변환하기

## 특수 객체 메서드 사용한 객체 형 변환

- **`hint(목표로 하는 자료형)`**를 기준으로 세 종류로 구분

### string

문자열을 기대하는 연산 수행시(`객체-문자형` 변환) ex.`alert`

```javascript
const user = {
    name : "Kate",
    age : 20
}
alert(user); // [object Object]
alert(typeof user); // object
//const stringUser = JSON.stringify(user);
//alet(stringUser); // {"name":"Kate","age":20}
```

### number

수학 연산을 적용할 때(`객체-숫자형` 변환)

```javascript
// 명시적 형 변환
const user = {
    name : "Kate",
    age : 20
}
let num = Number(user);
console.log(num); // NaN(Not a Number);

// 수학 연산 
let n = +user; 
consolel.log(n); // Nan
```

### default

연산자가 기대하는 자료형이 **`확실하지 않을 때`** (드물게 발생)

`Date` 객체를 `제외`한 모든 내장 객체는 대개 hint가 "default"일 때와 "number"일 때를 동일하게 처리

```javascript
const user1 = {
    name : "Kate",
    age : 20
}
const user2 = {
    name : "Jack",
    age : 25
}

// 이항 덧셈 연산 (hint - default)
let total = user1 + user2
console.log(total); // [object Object][object Object]
```

### 형 변환 알고리즘

1. 객체에 `obj[Symbol.toPrimitive]` 메서드가 있는지 찾고, 있으면 메서드 호출

2. 1에 해당하지 않고 hint가 "string"
    : `obj.toString()` 혹은 `obj.valueOf()`를 호출

3. 1과 2에 해당하지 않고, hint가 "number"나 "default"
    : obj.valueOf() 혹은 obj.toString() 호출

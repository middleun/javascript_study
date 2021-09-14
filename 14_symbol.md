# 심볼 (Symbol)

객체 속성(object property)을 만들 수 있는 원시 데이터 형식(primitive data type)

**`유일한 식별자(unique identifier)`**를 만들 때 사용

```javascript
// 새로운 심볼 a, b
const a = Symbol();
const b = Symbol();

console.log(a === b); // false
console.log(a == b); // false

// 심볼 이름 - 심볼에 대한 설명, 디버깅시 유용
const id1 = Symbol("id");
const id2 = Symbol("id");

consol.log(id1 = id2); // false, 설명이 동일하더라도 각 심볼값은 다름
```

## 객체 안의 심볼

`대괄호[]`를 사욯해 심볼형 키 생성

```javascript
const id = Symbol("id");
const user = {
    name : "Kate",
    age : 30,
    [id] : "katty"
}
console.log(user); //{name: 'Kate', age: 30, Symbol(id): 'katty'}
console.log(user[id]); // "Katty" 
```

## 숨김 프로퍼티(hidden property)

외부에 노출할 필요가 없는 프로퍼티 숨김 가능

`Object.keys(obj)`

`Object.values(obj)`

`Object.entries(obj)`

`for .. in`

으로 찾을 수 없음

But, **`Object.assign`**은 키가 심볼인 프로퍼티를 배제하지 않고 객체 내 모든 프로퍼티를 복사

## 전역 심볼

### **`Symbol.for(key)`**

조건에 맞는 심볼이 없으면 새로운 심볼을 만들고, 있으면 가져오기 때문에 `하나`의 심볼만 보장받을 수 있음

Symbol.for 메소드는 하나를 생성한 뒤 키를 통해 같은 Symbol을 `공유`

### **`Symbol.keyFor(key)`**

전역심볼을 찾을 때 사용

```javascript
const id1 = Symbol.for("id");
const id2 = Symbol.for("id");

console.log(id1 === id2); // true

Symbol.keyFor(id1); // 'id' , 생성할 때 적었던 이름을 알려줌
```

### 전역심볼이 아닐 때?

전역심볼이 아닌 심볼은 Symbol.for을 쓸 수 없음

**`description`** 사용

### 추가 reference

코딩앙마 유튜브

<https://www.youtube.com/watch?v=KF6t61yuPCY&ab_channel=%EC%BD%94%EB%94%A9%EC%95%99%EB%A7%88>

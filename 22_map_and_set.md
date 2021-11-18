# 맵과 셋(Map and Set)

## 맵(Map)

: **키**가 있는 데이터를 저장한다는 점에서 `객체`와 유사, but 키에 `다양한 자료형` 허용. 키의 타입에 **제약 X**

### 주요 메소드

- `new Map()` : 맵 생성

- `map.set(key, value)` : key를 이용해 value를 저장

- `map.get(key)` : `key`에 해당하는 값 반환, key가 존재하지 않으면 `undefined` 반환

- `map.has(key)` : key가 존재하면 `true`, 존재하지 않으면 `false` 반환

- `map.delete(key)` : key에 해당하는 값 `삭제`

- `map.clear()` : 맵 안의 **모든 요소** `제거`

- `map.size` : 요소의 `개수`를 반환

```javascript
let map = new Map();
console.log(map); // Map(0) {size: 0}

map.set("1", "str"); // 문자형
map.set(1, "num"); // 숫자형 
map.set(true, "bool") // 불린형

console.log(map.get(1)); // num - 키의 타입을 변환하지 않고 그대로 유지
console.log(map.get("1")); // str 
console.log(map.size); // 3

// 키로 객체를 허용
let user = {name : "June"};

let userLogInMap = new Map();

userLogInMap.set(user, 100); // 객체인 user를 키로 이용해 value 100을 저장

console.log(userLogInMap.get(user)); // 100 - key인 user에 해당하는 vaue 100을 반환
```

### 맵의 요소에 반복 작업하는 메소드

- `map.keys()` : 각 요소의 **키**를 모은 반복 가능한(iterable) 객체를 반환

- `map.values()` : 각 요소의 **값**을 모은 이터러블 객체를 반환

- `map.entries()` : 각 요소의 **[키, 값]**을 한 쌍으로 하는 이터러블 객체를 반환

## 셋(Set)

: **중복을 허용하지 않는 값**을 모아놓은 컬렉션으로 셋에 키가 없는 값이 저장

`값의 유일무이함`을 확인하는데 최적화

### 메소드

- `new Set(iterable)` : 셋 생성. 이터러블 객체(대개 배열)를 전달받으면 `값`을 `복사`해 셋에 저장

- `set.add(value)` : 값을 `추가`하고 셋 자신을 반환

- `set.delete(value)` : 값을 `제거`. 셋 내에 값이 존재해서 제거에 성공하면 true, 아니면 false 반환

- `set.has(value)` : 셋 내에 값이 존재하면 true, 아니면 false 반환

- `set.clear()` : 셋 안의 **모든 요소** `제거`

- `set.size` : 요소의 `개수` 반환

```javascript
let set = new Set();
let user = 
```

```javascript
// Q1. 배열에서 중복요소 제거
// 1st try
function unique(arr) {
    let set = new Set();
    for(let str of arr) {
        set.add(str);
    }
    return set;
}
let values = ["Hare", "Krishna", "Hare", "Krishna", "Hare", "Krishna", "Hare", "Hare", ":-0"];

console.log(unique(values)); // Set(3) {'Hare', 'Krishna', ':-0'}

// 2nd try
function unique(arr) {
    let set = new Set(arr);
    return set;
}
let values = ["Hare", "Krishna", "Hare", "Krishna", "Hare", "Krishna", "Hare", "Hare", ":-0"];

console.log(unique(values)); // Set(3) {'Hare', 'Krishna', ':-0'}

// answer of modernJStutorial
function unique(arr) {
  return Array.from(new Set(arr));
}
```

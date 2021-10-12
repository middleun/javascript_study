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

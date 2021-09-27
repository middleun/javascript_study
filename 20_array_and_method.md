# 배열과 메소드(Array and Method)

## 요소 추가/제거 메소드

`pop()` : 맨 끝 요소 추출

`push(...items)` : 맨 끝에 요소 추가

`shift()` : 맨 앞 요소 추출

`unshift(...items)` : 맨 앞에 요소 추가

### `splice`

배열에서 `특정 요소` 하나만 지울 때

`arr.splice(pos, deleteCount, [elem1, ..., elemN])`

- `pos` : 조작을 가할 첫 번째 요소의 위치

- `deleteCount` : 제거하고자 하는 요소의 개수

- `elem1, ..., elemN` : 배열에 추가할 요소

즉, `pos`부터 `deleteCount` 개의 요소를 지우고 `elem1,..,elemN`을 추가

```javascript
let arr = ["mon", "tue", "wed", "thu", "fri"];

// 특정요소 제거
// arr.splice(1, 2); 
// console.log(arr); // (3) ['mon', 'thu', 'fri']

// 특정요소 제거 후 추가
arr.splice(1, 2, "TUE", "WED"); 
console.log(arr); // (5) ['mon', 'TUE', 'WED', 'thu', 'fri']

// 제거한 요소 반환 
let result = arr.splice(1,2);
console.log(result); // (2) ['tue', 'wed']
```

### `slice`

`arr.slice(start, end)`

: `start`부터 `end` 바로 앞까지의 요소를 복사해 새로운 배열을 반환

```javascript
let arr = ["mon", "tue", "wed", "thu", "fri"];

arr.slice(1,3); // (2) ['tue', 'wed']

arr.slice(); // (5) ['mon', 'tue', 'wed', 'thu', 'fri'] 
```

### `concat`

`arr.concat(arg1, arg2...)`

: 기존 배열의 요소를 사용해 새로운 배열을 만들거나 기존 배열에 요소를 추가하고자 할 때 사용(합쳐서 새 배열 반환)

제공받은 배열의 요소를 복사해 활용

```javascript
let arr1 = [1, 2, 3];
let arr2 = [4, 5, 6];

alert(arr1.concat(arr2)); // 1,2,3,4,5,6
```

## 반복작업 : forEach

`arr.forEach`

배열 요소 **각각**에 대해 주어진 함수 실행 가능

```javascript
let days = ["mon", "tue", "wed", "thu", "fri", "sat", "sun"];
days.forEach((day, index) => {
    console.log(`${index + 1} . ${day}`);
});
// 1 . mon
// 2 . tue 
// 3 . wed 
// 4 . thu 
// 5 . fri 
// 6 . sat 
// 7 . sun
```

## 배열 탐색

### indexOf

`arr.indexOf(item, from)`

요소의 `위치` 탐색

: 인덱스 from부터 시작해 item(요소)을 탐색. 요소를 발견하면 해당 요소의 `인덱스` 반환, 발견하지 못하면 -1을 반환

### lastIndexOf

`arr.lastIndexOf(item, from)`

: 배열의 `끝`에서부터 탐색 시작

## 배열 변형

### map

`arr.map`

배열 요소 전체를 대상으로 함수 호출 및 호출 결과를 배열로 반환

```javasccript
let result = arr.mpa(function(item, index, array){
    // 요소 대신 새로운 값 반환
})
```

### sort(fn)

let arr1 = [1,2,3];
let arr2 = [4,5,6];

alert(arr1.concat(arr2)); //

``arr.sort()`
배열의 요소 정렬. 배열 `**자체**`가 변경됨

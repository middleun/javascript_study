# 배열과 메소드(Array and Method)

## 요소 추가/제거 메소드

`pop()` : 맨 끝 요소 추출

`push(...items)` : 맨 끝에 요소 추가

`shift()` : 맨 앞 요소 추출

`unshift(...items)` : 맨 앞에 요소 추가

### splice

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

### slice

`arr.slice(start, end)`

: `start`부터 `end` 바로 앞까지의 요소를 복사해 새로운 배열을 반환

```javascript
let arr = ["mon", "tue", "wed", "thu", "fri"];

arr.slice(1,3); // (2) ['tue', 'wed']

arr.slice(); // (5) ['mon', 'tue', 'wed', 'thu', 'fri'] 
```

### concat

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

```javascript
let arr = [1,2,3,4,5,1,2,3];

// indexOf - 배열의 처음에서부터 index 탐색
arr.indexOf(3); // 2 - 3의 index를 반환
arr.indexOf(3,3); // 7 - 3(두 번째 인수)부터 시작해서 3(첫 번째 인수)의 index를 반환 

// lastIndexOf - 배열의 끝에서부터 탐색
arr.lastIndexOf(3); // 7 - 끝에서 처음으로 만나는 3의 index
```

### includes

`arr.includes()`

: `포함`하고 있는지만 확인하고 싶을 때 사용. 배열에 요소가 있으면 true, 그렇지 않으면 false 반환

```javascript
let arr = [1,2,3,4,5];

arr.includes(3); // true
arr.includes(6); // false
```

### find

`arr.find(fn)`

객체로 이루어진 배열 안에서 특정 조건에 부합하는 객체를 찾고 싶을 때 사용

```javascript
let result = arr.find(function(item, index, array){
});
// index, array 인자는 잘 사용되지 않음
```

함수가 **true**를 반환하면 `해당 요소` 반환하고 탐색 끝, 원하는 요소를 찾지 못하면 `undefined`를 반환

```javascript
// ex 1
let arr = [1,2,3,4,5,6];

let result = arr.find((item) => {
    return item % 2 === 0;
});
console.log(result); // 2 - 첫번째 trun값만 반환하고 탐색 중단! 모든 값을 반환하고 싶다면 filter 사용

// ex 2
let users = [
    { id: 1, name: "Ann", age: 20 },
    { id: 2, name: "John", age: 27 },
    { id: 3, name: "Mack", age: 15 }
];

let result = users.find((user) => {
    if (user.age < 19){
        return true; 
    }
    return false;
});

console.log(result); // {id: 3, name: 'Mack', age: 15}

let result2 = users.find(user => user.id == 2);

console.log(result2); // {id: 2, name: 'John', age: 27}
console.log(result2.name); // John
```

### findIndex

`arr.findIndex(fn)`

조건에 맞는 해당 요소의 `인덱스`를 반환, 조건에 맞는 요소가 없으면 `-1` 반환

### filter

`arr.filter(fn)`

조건에 맞는 모든 요소를 배열로 반환

```javascript
// ex 1
let arr = [1,2,3,4,5,6];

let result = arr.filter((item) => {
    return item % 2 === 0;
});
console.log(result); // (3) [2, 4, 6] - 조건에 만족하는 모든 요소(짝수)를 배열로 반환 
```

## 배열 변형

### map

`arr.map(fn)`

모든 요소에 함수를 호출하고 반환된 결과를 `새로운 배열`로 반환

```javascript
let users = [
    { id: 1, name: "Ann", age: 20 },
    { id: 2, name: "John", age: 27 },
    { id: 3, name: "Mack", age: 15 }
];

let newUsers = users.map((user, index) => {
    return Object.assign({}, user, {
        id: index + 1,
        isAdult: user.age > 19,
    });
});

console.log(newUsers); // (3) [{…}, {…}, {…}]
// 0: {id: 1, name: 'Ann', age: 20, isAdult: true}
// 1: {id: 2, name: 'John', age: 27, isAdult: true}
// 2: {id: 3, name: 'Mack', age: 15, isAdult: false}

console.log(newUsers[0].isAdult); // true
```

### sort(fn)

`arr.sort()`

배열 **`자체`**가 변경

```javascript
let arr1 = [1,2,3];
let arr2 = [4,5,6];

console.log(arr1.concat(arr2)); // (6) [1, 2, 3, 4, 5, 6]
console.log(arr2.concat(arr1)); // (6) [4, 5, 6, 1, 2, 3]

```

### reverse

`arr.reverse()`

: arr의 요소를 **역순**으로 재정렬

```javascript
let arr = [1,2,3,4,5];

arr.reverse(); // (5) [5, 4, 3, 2, 1]
```

### join

`arr.join(glue)`

: 배열을 `문자열`로 변환

인수 glue를 접착제처럼 사용해 배열 요소를 모두 합친 후 하나의 문자열로 변환

```javascript
let arr = ["Ann","John","Mack","Jack"];

let result = arr.join();
console.log(result); // Ann,John,Mack,Jack

let result2 = arr.join(";");
// ; 를 사용해 배열 요소 모두를 하나의 문자열로 합침
console.log( result2 ); // Ann;John;Mack;Jack
```

### split

`str.split(delim)`

: 문자열을 `배열`로 변환

구분자(delimiter) `delim`을 기준으로 문자열을 쪼개줌

```javascript
let users = "Ann, John, Mack, Jack";

let result = users.split(","); // ,(쉼표)를 기준으로 문자열을 쪼개서 배열로 변환

console.log(result); // (4) ['Ann', ' John', ' Mack', ' Jack']

// delim을 빈 문자열로 정할 경우
let str = "sample";
console.log( str.split("") ); // (6) ['s', 'a', 'm', 'p', 'l', 'e'] - 빈 문자열을 기준으로 자르기 때문에, 문자열을 글자 단위로 분리
```

### reduce

### reduceRight

### 추가 reference

코딩앙마 유튜브

<https://www.youtube.com/watch?v=pJzO6O-aWew&t=15s&ab_channel=%EC%BD%94%EB%94%A9%EC%95%99%EB%A7%88>

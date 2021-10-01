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

: 배열 요소 **각각**에 대해 주어진 함수 실행 가능

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

: 요소의 `위치` 탐색

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

: 객체로 이루어진 배열 안에서 특정 조건에 부합하는 객체를 찾고 싶을 때 사용

```javascript
let result = arr.find(function(item, index, array){
});
// index, array 인자는 잘 사용되지 않음
```

: 함수가 **true**를 반환하면 `해당 요소` 반환하고 탐색 끝, 원하는 요소를 찾지 못하면 `undefined`를 반환

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

: 조건에 맞는 해당 요소의 `인덱스`를 반환, 조건에 맞는 요소가 없으면 `-1` 반환

### filter

`arr.filter(fn)`

: 조건에 맞는 `모든` 요소를 배열로 반환

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

: 모든 요소에 함수를 호출하고 반환된 결과를 `새로운 배열`로 반환

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

** map 심화학습 필요!

### sort

`arr.sort(fn)`

: 배열을 재정렬, 배열 **`자체`**가 변경됨

```javascript
// ex1, 숫자
let arr1 = [1,3,5,4,2];

arr1.sort();
console.log(arr1); // (5) [1, 2, 3, 4, 5]

// ex2, 문자열
let arr2 = ["a","e","d","b","c"];

arr2.sort();
console.log(arr2); // (5) ['a', 'b', 'c', 'd', 'e']

// ex3
let arr3 = [20, 5, 1, 37];

arr3.sort();
console.log(arr3); // (4) [1, 20, 37, 5]
// 배열을 정렬할 때 요소를 문자열로 취급하기 때문에 '5' > '3'7
```

sort에 **`정렬 함수`**를 인수로 넘겨주지 않으면 위의 `ex3`과 같이 사전편집 순으로 요소를 정렬

```javascript
// 오름차순 정렬하고 싶을 때
let arr = [20, 5, 1, 37];

// 방법1. 값을 비교할 수 있는 함수를 인수로 넘겨줌
function fn(a,b) {
    return a - b; 
    // a와 b 두 요소의 값을 비교, a가 작으면 a를 앞으로 보내고 a = b, 즉 0을 반환하면 그대로, b가 작으면 b를 앞으로 보냄
}

arr.sort(fn); // 함수 fn을 인수로 전달

// 방법2. 더 간단하게 
arr.sort((a, b) => {
    return a - b;
});

// 방법3. 더 더 간단하게 
arr. sort((a, b) => a - b); // 두 요소를 비교
console.log(arr); // (4) [1, 5, 20, 37]
```

- `lodash`라이브러리 사용할 경우, `.sortBy(arr);`

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

`arr.reduce(fn)`

`function((누적 계산값, 현재값) => { return 계산값 }, 초기값);`

: 배열을 기반으로 값 하나를 도출할 때 사용

```javascript
// 배열의 모든 수 합치기 
// for, for...of, forEach 등의 방법
let arr = [1,2,3,4,5];

// forEach 사용할 경우
let result = 0;
arr.forEach((num) => {
    result += num;
});

console.log(result); // 15

// reduce 사용할 경우
let result = arr.reduce((prev, cur) => {
    return prev + cur;
    // prev : 이전에 누적된(현재까지 누적된) 계산값, cur : 현재값
}, 0); // 0: 초기값 - 옵션

// 초기값 0에서 시작 -> (0, 1) => {return 0 + 1;} //1
// 한 바퀴 돌고 다시 (1, 2) => {return 1 + 2;} //3
// (3, 3) => {return 3 + 3;} // 6
// (6, 4) => {return 6 + 4;} // 10
// (10, 5) => {return 10 + 5}; // 15
// 이런식으로! 인수로 넘겨주는 함수가 배열의 모든 요소를 대상으로 차례차례 적용!!
```

초기값은 옵션이기 때문에 안 들어가도 상관없으나, 배열이 비어있는 상태일 경우 reduce호출시 에러가 발생할 수 있으므로 `초기값`을 **명시**해줄 것을 권장!

```javascript
// user 리스트에서 성인만 뽑아서 새로운 배열을 만들 때 

let users = [
    { id: 1, name: "Ann", age: 20 },
    { id: 2, name: "John", age: 27 },
    { id: 3, name: "Mack", age: 15 },
    { id: 4, name: "Jane", age: 19 },
    { id: 5, name: "Ben", age: 45 },
    { id: 6, name: "Kate", age: 32 }
];

let result = users.reduce((prev, cur) => {
    // 성인만 추출해내는 if문 작성- 현재 객체(cur)의 age 판단
    if(cur.age > 19){
        // 지금까지 만들어진 배열(prev)에 push 
        prev.push(cur.name);
    }
    return prev; // 미성년자일 경우 if문 이하를 실행하지 않고 지금까지 만들어진 배열(prev)이 그대로 실행
}, []); // 초기값을 빈 배열로 두고 값이 추가되도록

console.log(result); // (4) ['Ann', 'John', 'Ben', 'Kate']
// user리스트에서 성인만 따로 뽑아서 새로운 배열 추출!
```

### reduceRight

`arr.reduceRight(fn)`

: reduce와 동일한 기능, but 배열의 **오른쪽**부터 연산을 수행

## 배열 여부 알아내기

### Array.isArray()

: js에서 배열은 객체형에 속하므로, `typeof`로는 객체와 배열 구분이 어려움

: 배열이며 `true`, 배열이 아니면 false 반환

```javascript
let user = {
    name : "Ann",
    age : 20,
}; // 객체

let users = ["Ann", "John", "Mack"]; // 배열

// typeof 사용
console.log(typeof(user)); // object
console.log(typeof(users)); // object

// Array.isArray 사용
console.log(Array.isArray(user)); // false
console.log(Array.isArray(users)); // true
```

---

### 추가 reference

코딩앙마 유튜브

<https://www.youtube.com/watch?v=pJzO6O-aWew&t=15s&ab_channel=%EC%BD%94%EB%94%A9%EC%95%99%EB%A7%88>

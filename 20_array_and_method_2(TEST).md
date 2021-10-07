# 배열과 메소드 예제

## Q1. border-left-width => borderLeftWidth

: 문자열을 배열로 - `split`, 배열을 다시 문자열로 - `join`

```javascript
// 1. 문자열을 배열로 쪼개기
function camelize(str) {
    return str.split("-");
}

camelize("background-color"); // (2) ['background', 'color']
camelize("list-style-image"); // (3) ['list', 'style', 'image']
camelize("-webkit-transiton"); // (3) ['', 'webkit', 'transiton']

// 2. 매핑하기 ( 각 단어의 첫번째 글자 대문자로 )
function camelize(str) {
    return str.split("-").map((word, idx) => {
        if(idx == 0){
            return word;
        } else {
            return word[0].toUpperCase() + word.slice(1)
        }
    });
}

camelize("background-color"); // (2) ['background', 'Color']
camelize("list-style-image"); // (3) ['list', 'Style', 'Image']
camelize("-webkit-transiton"); // (3) ['', 'Webkit', 'Transiton']

// 3. 배열을 다시 문자열로
function camelize(str) {
    return str.split("-").map((word, idx) => {
        if(idx == 0){
            return word;
        } else {
            return word[0].toUpperCase() + word.slice(1)
        }
    }).join("");
}

camelize("background-color"); // 'backgroundColor'
camelize("list-style-image"); // 'listStyleImage'
camelize("-webkit-transiton"); // 'WebkitTransiton' 
```

## Q2. 특정범위에 속하는 요소 찾기

: `filter`? (O)

```javascript
function filterRange(arr, a, b) {
    return arr.filter((item) => {
        return a <= item && item <= b
        // 가독성을 위해 한 줄로 표현하면.
        // return arr.filter(item => (a <= item && item <= b));
    });
}
let nums = [5, 3, 8, 1];
let filtered = filterRange(nums, 1, 4);

console.log(filtered); // (2) [3, 1]
console.log(arr); // (4) [5, 3, 8, 1] - 기존 배열 변형 X!!!
```

## Q3. 특정범위에 속하는 요소 찾기(기존 배열 변경)

: `splice` (O)

```javascript

//** 1st try **//
// arr의 요소 중 a와 b 사이에 속하지 않는 요소는 삭제해주는 함수
function filterRangeInPlace(arr, a, b){
    for(i = 0; i < arr.length; i++) {
        if(!a <= arr[i] && arr[i] <= b){
            arr.splice(i, 1);
        }
    }
}

let arr = [5, 3, 8, 1];

filterRangeInPlace(arr, 1, 4);

console.log(arr); // (2) [5, 8] (반대로 나와버렸네..!?)

//** 2nd try **//
// arr의 요소 중 a와 b 사이에 속하지 않는 요소는 삭제해주는 함수
function filterRangeInPlace(arr, a, b){
    for(i = 0; i < arr.length; i++) {
        if(a <= arr[i] && arr[i] <= b){
            return;
        } else {
            arr.splice(i, 1);
        }
    }
}

let arr = [5, 3, 8, 1];

filterRangeInPlace(arr, 1, 4);

console.log(arr); // (2) [3, 1]

//** 모던javascript 해답 **//
function filterRangeInPlace(arr, a, b) {
  for (let i = 0; i < arr.length; i++) {
    let val = arr[i];

    // 범위 밖의 요소를 제거함
    if (val < a || val > b) {
      arr.splice(i, 1);
      i--;
    }
  }
}

let arr = [5, 3, 8, 1];

filterRangeInPlace(arr, 1, 4); // 1과 4 사이에 있지 않은 요소는 모두 제거함

alert( arr ); // [3, 1] - 기존 배열 변형 !

```

## Q4. 내림차순 정렬

: 정렬이니까 `sort`! (O)

```javascript
//** 1st try **//
let arr = [5, 2, 1, -10, 8];

arr.sort((a, b) => a - b);

console.log(arr); // (5) [-10, 1, 2, 5, 8] (아. '내림차순'..!)

//** 2nd try **//
let arr = [5, 2, 1, -10, 8];

arr.sort((a, b) => b - a);

console.log(arr); // (5) [8, 5, 2, 1, -10]
```

## Q5. 배열 복사본 정렬

: 복사본 - `silce`, 정렬 - `sort` (O)

```javascript
function copySorted(arr) {
    // 문자열 담긴 배열 arr을 복사(slice) 후 정렬(sort)
    return arr.slice().sort();
}

let arr = ["HTML", "Javascript", "CSS"];

let sorted = copySorted(arr);

console.log(sorted); // (3) ['CSS', 'HTML', 'Javascript']
console.log(arr); // (3) ['HTML', 'Javascript', 'CSS']
```

## Q6. 이름 매핑

: 매핑. `map` (O)

```javascript
// name의 값만 담은 새로운 배열 
let john = {name: "John", age: 25};
let pete = {name: "Pete", age: 30};
let mary = {name: "Mary", age: 28};

let users = [ john, pete, mary ];

let names = users.map(user => user.name);
console.log(names); // (3) ['John', 'Pete', 'Mary']
```

## Q7. 객체 매핑

```javascript
// Q7 - 객체 매핑 : map
let john = {name: "John", surname: "Smith", id: 1};
let pete = {name: "Pete", surname: "Hunt", id: 2};
let mary = {name: "Mary", surname: "Key", id: 3};

let users = [ john, pete, mary ];

let usersMapped = users.map(user => {
    return Object.assign({}, {
        fullName : `${user.name} ${user.surname}`,
        id: user.id
    });
});

console.log(usersMapped); // (3) [{…}, {…}, {…}]
// 0: {fullName: 'John Smith', id: 1}
// 1: {fullName: 'Pete Hunt', id: 2}
// 2: {fullName: 'Mary Key', id: 3}
console.log(usersMapped[0].id); // 1
console.log(usersMapped[2].fullName); // Mary Key
```

## Q8. 나이 기준 객체 정렬

`sort`

```javascript
function sortByAge(arr) {
    arr.sort((a, b) => a.age - b.age);
}

let john = {name: "John", age: 25};
let pete = {name: "Pete", age: 30};
let mary = {name: "Mary", age: 28};

let arr = [ pete, john, mary ];

sortByAge(arr);

console.log(arr);
console.log(arr[0].name); // John
console.log(arr[1].name); // Mary
console.log(arr[2].name); // Pete
```

## Q9. 평균 나이 구하기

: forEach? reduce? .... `reduce`!

```javascript
function getAverageAge(users){
    return users.reduce((prev, user) => prev + user.age, 0) / users.length;
}

let john = {name: "John", age: 25};
let pete = {name: "Pete", age: 30};
let mary = {name: "Mary", age: 28};

let arr = [ john, pete, mary ];

console.log( getAverageAge(arr) ); // 27.666666666666668

let result = getAverageAge(arr);

console.log(Math.ceil(Number(result))); // 28
```

## Q10. 배열 내 중복되는 요소 탐색

```javascript
function unique(arr) {
    // 1. 새로운 배열 생성
    let result = [];

    for(str of arr){
        // 2. 새로운 배열 안에 요소가 있는지 확인, 없다면
        if(!result.includes(str)) {
            // 3. 새로운 배열에 요소를 push 
            result.push(str);
        }
    }
    return result;
    console.log(result);
}

let strings = ["Hare", "Krishna", "Hare", "Krishna", 
"Krishna", "Krishna", "Hare", "Hare", ":-0"];

console.log( unique(strings) ); // (3) ['Hare', 'Krishna', ':-0']
```

## Q11

```javascript
function groupById(users){
    users.reduce((object, value) => {
        object[value.id] = value;
        return object;
    },{}) // 빈 객체를 초기값으로
}

let users = [
    {id: 'john', name: "John Smith", age: 20},
    {id: 'ann', name: "Ann Smith", age: 24},
    {id: 'pete', name: "Pete Peterson", age: 31},
];

let userById = groupById(users);
console.log(userById);
```

## + 예제 풀이 more and more

```javascript
// 1차 시도
function divideArrayInHalf(array) {
    let result = [];
    for(let i = 0; i < array.length; i++) {
        if(array[i] = 10 || array[i] <= 10){
            result.unshift(array[i]);
        } else {
            result.push(array[i]);
        }
    }
    return result;
    console.log(result);
}

let array = [1, 20, 10, 5, 100];
divideArrayInHalf(array);
console.log(array); // (5) [10, 10, 10, 10, 10]
// console.log(result);
```

## codewars 예제 풀이(Kata)

- Sort and Star (-ing)

> You will be given a vector of strings. You must sort it **`alphabetically`** (case-sensitive, and based on the ASCII values of the chars) and then return the **`first value`**.
>
> The returned value must be a **`string`**, and have `"***"` `between each of its letters`.
>
> You should **not remove or add** elements from/to the array.

```javascript
function twoSort(s) {
  // 배열 알파벳순으로 정렬 후 첫 번째 요소 반환. 추출?
    let result = s.sort().splice(0,1).join();
    return result;
}

let arr = ["bitcoin", "take", "over", "the", "world", "maybe", "who", "knows", "perhaps"];
twoSort(arr); // 'bitcoin'

```

### 추가 reference / 예제 출처

JavaScript 연습 문제 - velog

<https://velog.io/@jinjinhyojin/JavaScript-%EC%97%B0%EC%8A%B5-%EB%AC%B8%EC%A0%9C>

Training on Sort and Star | Codewars

<https://www.codewars.com/kata/57cfdf34902f6ba3d300001e/train/javascript>

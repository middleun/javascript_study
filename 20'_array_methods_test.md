# 배열과 메소드 예제

```javascript
// Q1 border-left-width -> borderLeftWidth
let str = "background-color"

let splitStr = str.split("-");
console.log(splitStr);

```

```javascript
// Q2 - 특정 범위에 속하는 요소 찾기 : filter? 

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

```javascript
// Q3 - 특정 범위에 속하는 요소 찾기(기존 배열 변경) : splice

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

```javascript
// Q4 - 내림차순 정렬 : sort!

//** 1st try **//
let arr = [5, 2, 1, -10, 8];

arr.sort((a, b) => a - b);

console.log(arr); // (5) [-10, 1, 2, 5, 8] (아. '내림차순'..!)

//** 2nd try **//
let arr = [5, 2, 1, -10, 8];

arr.sort((a, b) => b - a);

console.log(arr); // (5) [8, 5, 2, 1, -10]
```

```javascript
// Q5 - 배열 복사본 정렬
function copySorted(arr) {
    // 문자열 담긴 배열 arr을 복사(slice) 후 정렬(sort)
    return arr.slice().sort();
}

let arr = ["HTML", "Javascript", "CSS"];

let sorted = copySorted(arr);

console.log(sorted); // (3) ['CSS', 'HTML', 'Javascript']
console.log(arr); // (3) ['HTML', 'Javascript', 'CSS']
```

```javascript
// Q6 - 이름 매핑 : map

// name의 값만 담은 새로운 배열 
let john = {name: "John", age: 25};
let pete = {name: "Pete", age: 30};
let mary = {name: "Mary", age: 28};

let users = [ john, pete, mary ];

let names = users.map(user => user.name);
console.log(names); // (3) ['John', 'Pete', 'Mary']

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

console.log(usersMapped);
console.log(usersMapped[0].id);
console.log(usersMapped[0].fullName);
```

```javascript
// Q8 - 나이 기준 객체 정렬 - sort 
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

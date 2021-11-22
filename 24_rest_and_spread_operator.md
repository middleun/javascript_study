# 나머지 매개변수와 전개 문법(Rest parameters and Spread syntax)

## 나머지 매개변수 `...`

> [변수에 배열/객체의 나머지 할당](23_destructuring_assignment.md#변수에-배열객체의-나머지-할당)

`...` : "여분의 매개변수들을 한데 모아 배열에 집어넣어라"

> 전개는 배열을 그 엘리먼트로 '확장'하는 반면, 나머지는 여러 엘리먼트를 수집하며 이를 하나의 엘리먼트로 **'압축'**합니다. - [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax#나머지_구문_(매개변수))

인수 개수에 제한이 없는 함수를 만들 때

## 전개 구문(Spread Syntax)

> **전개 구문**을 사용하면 배열이나 문자열과 같이 반복 가능한 문자를 0개 이상의 인수(함수로 호출할 경우) 또는 요소(배열 리터럴의 경우)로 확장하여, 0개 이상의 키-값의 쌍으로 객체로 **확장**시킬 수 있습니다. - [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Spread_syntax)

다수의 인수를 받는 함수에 배열을 전달할 때

```javascript
// 배열을 대상으로 Math.max(최대값)을 호출하고 싶을 때
let arr = [3, 5, 10, 6];

console.log(Math.max(arr)); // NaN - Math.max는 배열이 아닌 숫자를 인수로 받기 때문

// 이럴 때 spread operator 사용 ! 
console.log(Math.max(...arr)); // 10 - spread를 사용하여 배열을 인수 목록으로 바꿔줌
```

배열을 합칠 때

```javascript
let arr1 = [3, 5, 1];
let arr2 = [2, 4, 6];

function merged(a, b){
    let newArr = [0, ...a, 2, ...b];
    return newArr.sort((a, b) => a - b);
} 

merged(arr1, arr2); // (8) [0, 1, 2, 2, 3, 4, 5, 6]
```

# 화살표함수(Arrow Function)

```javascript
let func = (arg1, arg2, arg3) => (expression)
```

```javascript

let sum = function(a,b){
    return a + b;
}

// 화살표 함수로 바꾸면?
let sum = (a,b) => a + b;
 
```

## 본문이 한 줄일 때

중괄호 없이 사용
`(args) => expression`

## 본문이 여러 줄일 때

중괄호와 함께 사용
`(args) => {body}`
반드시 return 지시자 사용하여 결괏값 반환

```javascript
let sum = (a,b) => {
    let result = a + b;
    // return 으로 결괏값 반환 
    return result;
}
```

```javascript
//Q1
function ask(question, yes, no){
    if(confirm(question)) yes()
    else no();
}

ask(
    "정말로 삭제하시겠습니까?",
    () => alert("삭제되었습니다"),
    () => alert("취소되었습니다")
); 

// Q2 (화살표함수로 바꿔보기)
const add = function (num1, num2) {
    const result = num1 + num2;
    return result;
}

// 화살표함수로 바꾸면?
const add = (num1, num2) => {
    const result = num1 + num2;
    return result;
}

// 더 간단하게 
const add = (num1, num2) => {
    return num1 + num2;
}

// const add = (num1, num2) => (num1 + num2); 
```

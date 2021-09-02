# 함수

## 함수선언(function declaration)

```javascript
function name(parameters) {
    함수본문;
}

function showGreeting() {
    alert("Welcome");
}
showGreeting(); // 호출
```

## 지역변수(local) & 전역변수(global)

- 지역변수 : 함수 안에서 접근

- 전역변수 : 함수 외부에서 접근

## 매개변수(parameter)

: 임의의 데이터를 함수 안에 전달할 때

cf. 매개변수 vs 인수(argument)

> - function parameters are the names listed in the function's definition
>- function arguments are the real values passed to the function
>- parameters are initialized to the values of the arguments supplied

출처 : [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Functions/arguments)

즉, 파라미터는 함수 선언시 정의된 변수(valuable),

인수는 함수를 호출할 때 전달되는 실제 값(value)!

```javascript
function showGreeting(name,text){ //parameter
    alert( name + "," + text );
}
showGreeting("june", "hello")//argument
```

## 반환값(return value)

- return

```javascript
function sum(a,b){
    return a+b;
}
let result = sum(1,2);
alert(result); //3
```

## 함수 이름짓기

- 어떤 동작을 하는지 설명할 수 있는 동사를 접두어로

- naming rule

## 함수 == 주석

- 간결하고, 한 가지 기능만 수행할 수 있는 함수

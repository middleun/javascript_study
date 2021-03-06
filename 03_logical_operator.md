# 논리연산자

## || (OR)

인수 중 `하나라도` true이면 true 반환, `아니면` false 반환

주어진 조건 중 "`하나라도`" 참인지 테스트하는 용도로 많이 쓰임 ( ex. if문 )  ---> **첫번째 TRUTHY**를 찾는 연산자

- OR연산자와 피연산자가 여러개인 경우, 가장 왼쪽 피연산자 -> 오른쪽으로 피연산자 평가

- 각 피연산자 불린형으로 변환 후 true -> 원래 값 반환

- 모든 피연산자가 false로 평가 -> 마지막 피연산자 반환

```javascript
console.log( 1 || 0 ); // 1

console.log( null || 1 ); // 1 ( null-F/ 1- T)

console.log( null || 0 || 1 ); // 1 ( null- F/ 0 - F/ 1-T )

console.log( null || undefined || 0 ); // 0 ( null - F/ undefined - F/ 0 - F. 모두 False인 경우 마지막값 반환!)
```

`단락평가`

: **truthy**를 만나면 나머지 값 건드리지 않은 채 평가 stop

## && (AND)

두 피연산자가 `모두` 참일 때 true 반환, 그 외는 false ---> **첫번째 FALSY**를 찾는 연산자

- 가장 왼쪽 피연산자 -> 오른쪽으로 피연산자 평가

- 불린형으로 변환 후 false -> 원래 값 반환

- 모든 피연산자가 true로 평가 -> 마지막 피연산자 반환

```javascript
console.log( 1 && 0 ); // 0 ( 1-T )

console.log( null && 1 ); // null ( null-F/ 두번째 피연산자 무시 )

console.log( 1 && undefined && 5 ); // undefined ( 1-T/ undefined- F/ 5 는 무시 )

console.log( 1 && 3 && 5 ); // 5 ( 1-T / 2-T / 3-T. 모두 True인 경우 마지막값 반환!)
```

**우선순위 : ` &&  > || `**

## ! (NOT)

```javascript
console.log( !true ); // false

console.log( !0 ); // true
```

```javascript
// Q1 - alert( null || 2 || undefined );의 결과?
// 2 ( || - truthy 찾을 때까지 )

// Q2 - alert( 1 && null && 2);의 결과?
// null ( && - falsy 찾을 때까지 )

// cf. alert - 창에 메시지를 띄어줄 뿐, 의미 있는 값을 반환하지 X. so, undefined 반환

// Q3 -  alert( null || 2 && 3 || 4 ); 의 결과?
//  &&이 먼저 실행.
// 1. 2 && 3 = 3 (둘다 truthy, 마지막값 반환)
// 2. null || 3 || 4 = 3 ( null - F, 3 - 첫번째T)

// Q4 - age가 14세 이상 90세 이하?
if( age >= 14 && age <= 90 )

// Q5
// 1 
if(!age >= 14 && age <= 90 )
// 2 
if( age > 14 || age > 90 )

// Q6
let userId = prompt("Enter your id");
if (userId == "" || userId == null || userId == undefined) {
    alert("Canceled");
} else if (userId == "Admin") {
    let userPw = prompt("Enter your password :(");
    if (userPw == "" || userPw == null || userPw == undefined) {
        alert("Canceled");
    } else if (userPw == "TheMaster") {
        alert("Welcome Admin!");
    } else {
        alert("Wrong Password");
    }
} else {
    alert("I don't know you");
}
```

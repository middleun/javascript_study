# 반복문(loops)

## null 병합연산자

`??`

: '값이 할당된' 변수를 빠르게 찾을 수 있음

`a ?? b`

: a가 null도 아닌 undefined도 아니라면 **a**

: 그 외는 **b**

```javascript
let userId = null;
let userPw = null;
let userName = "Joy";

console.log(userId ?? userPw ?? userName ?? "anonymous"); // Joy
// 세 변수 중 실제 값이 있는 변수 => userName = "Joy"
```

## for, while 반복문

### 1. while

조건문이 `참일 때만` 반복문 body 실행

```javascript
while (condition) {
    반복문 body
}
```

### 2. do ... while

조건문이 참인가에 상관없이 본문을 `'최소한 한 번이라도'` 실행하고 싶을 때

```javascript
do {
    반복문 body
} while (condition);
```

### 3. for

세미콜론( ; ) 필수

반복문의 조건이 `falsy가 될 때까지` 반복

```javascript
for (begin; condition; step) {
    // begin : 초기값, condition: 조건, step: 코드 실행 후 작업
    반복문 body
}

for (let i = 0; i < 10; i++) {
    consol.log(i);
}
```

- **`break`**

    break를 사용해서 반복문 중간에 언제든 빠져나올 수 있음

    ```javascript
    let sum = 0;
    while (true) {
        let value = +prompt("숫자를 입력하세요", "");
        if (!value) break;

        sum += value;
    }
    alert ("합계 : " + sum);
    // 입력되는 value 값이 없을 때까지 입력된 숫자의 합을 계산 
    // value 값이 없거나 취소를 누른 경우 반복문을 "빠져나와서" 그 다음 줄 실행. 즉, alert 실행
    ```

- **`continue`**

    break의 가벼운 버전

    현재 반복문을 멈추고 다음 반복으로 넘어가고 싶을 때 사용

    전체 반복문을 멈추는 것이 X,  "`조건을 통과`"

    ```javascript
    for (let i = 0; i < 10; i++ ) {
        if (i % 2 == 0) continue; // 나머지가 0인 수 일 때 continue (실행 중단 -> 다음 실행)
        console.log(i); // 1,3,5,7,9
    }
    ```

- break, continue -> 삼항 연산자에 사용 **X**

- **`label`**

    여러 개의 중첩 반복문을 한 번에 빠져나와야 할 때!

    `break <labelName> or continue <labelName>`

## switch문

복수의 if문 -> switch문

`하나 이상의 case문`으로 구성

break문을 만나기 전까지의 모든 구문을 다 실행

```javascript
    switch(x){
        case 'value1' :
        ...
        [break]

        case 'value2' :
        ...
        [break]

        default :
        ...
        [break]
    }
    // 변수 x의 값과 일치하는 값을 case문에서 찾으면 case문 아래 코드 실행
    // but, x의 값과 일치하는 case문이 없으면 default문 아래의 코드 실행 (like 'if문의 else')

    let drink = prompt("어떤 커피를 원하시나요?");

    switch(drink) {
        case "아메리카노" :
            console.log("100원입니다");
            break;

        case "바닐라라떼" :
            console.log("200원입니다");
            break;

        case "콜드브루" :
            console.log("300원입니다");
            break;
        case "아인슈페너" :
        case "카페모카" :
            console.log("400원입니다");
            break;
        default :
            console.log("원하시는 메뉴가 없습니다");
    }
```

```javascript
//Q1 (짝수만 출력)
for (let i = 2; i <= 10; i++) {
    if (i % 2 == 0);
    alert(i);
}

//Q2( for->while )
let i = 0;
while (i < 3) {
    alert(`number ${i}!`);
    i++;
}

//Q3
while (true) {
    let i = prompt("Q3.100을 초과하는 값을 입력하세요", 0);
    if (i > 100 || !i) break;
}

// Q4 (소수 출력)
function getPrime(n) {
    for (let i = 2; i <= n; i++) {
        if (i % 2 == 0) continue;
        console.log("Q4." + i);
    }
}
getPrime(100);
// ->ㄴㄴㄴㄴㄴㄴㄴ / 소수 판별 알고리즘 찾아보기
// cf. 중첩 반복문 사용
// 범위 내 모든 숫자 i에 대해서 {
//     1과 i 사이에 제수(나눗수)가 있는지 확인
//     있으면 => 소수가 아님
//     없으면 => 소수이므로 출력
// }
```

### 추가 reference

코딩앙마 유튜브

<https://www.youtube.com/watch?v=KF6t61yuPCY&ab_channel=%EC%BD%94%EB%94%A9%EC%95%99%EB%A7%88>

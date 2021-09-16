# 숫자형

## 숫자 입력

### `e`

- **e 왼쪽의 수 * 10 <sup>e 오른쪽에 있는 수</sup>**

    ```javascript
    let num = 8e5 // = 8 * 100000
    console.log(num); // 800000
    ```

- e 우측에 `음수`가 있는 경우, **e 왼쪽의 수 / 10 <sup>e 오른쪽에 있는 수</sup>**

    ```javascript

    let ms = 0.000001; // 1마이크로초 - 백만분의 1초
    // e를 사용
    let ms = 1e-6; // 1 / 100000
    console.log(ms);  
    ```

### 16진수, 2진수, 8진수

- 16진수 : **`0x`**

```javascript
console.log( 0xff ); //
```

- 2진수 : `0b` / 8진수 : `0o`

### `toString(base)`

`base` 진법으로 `num`을 표현한 후 이를 `문자형`으로 변환해 반환

```javascript
let num = 255;

console.log( num.toString(16) ); // ff
console.log( num.toString(2) ); // 11111111
```

- `base=16`

    16진수 색, 문자 인코딩 등

     숫자는 0 ~ 9, 10이상의 수는 A ~ F

- `base=2`

    비트 연산 디버깅, 0 또는 1

- `base=36`

    사용할 수 있는 base 중 최댓값

### 어림수 구하기(rounding)

- **`Math.floor`**

    소수점 첫째 자리에서 내림(버림)

- **`Math.ceil`**

    소수점 첫째 자리에서 올림

- **`Math.round`**

    소수점 첫째 자리에서 반올림

- **`Math.trunc`**

    소수부를 무시( IE 지원 X)

    ```javascript
    let num1 = 3.1
    let num2 = -1.1
    let num3 = 3.6

    // Math.floor
    console.log(Math.floor(num1)); // 3
    console.log(Math.floor(num2)); // -2
    console.log(Math.floor(num3)); // 3

    // Math.ceil
    console.log(Math.ceil(num1)); // 4
    console.log(Math.ceil(num2)); // -1
    console.log(Math.ceil(num3)); // 4

    // Math.round
    console.log(Math.round(num1)); // 3
    console.log(Math.round(num2)); // -1
    console.log(Math.round(num3)); // 4

    // Math.trunc
    console.log(Math.trunc(num1)); // 3
    console.log(Math.trunc(num2)); // -1
    console.log(Math.trunc(num3)); // 3
    ```

- **`toFixed(n)`**

    부정확한 계산을 해결할 때 가장 신뢰할 수 있는 방법

    >숫자는 0과 1로 이루어진 이진수로 변환되어 연속된 메모리 공간에 저장되는데, 이 때 0.1같은 분수는 이진법으로 표현하면 무한소수가 되는 문제 발생 => 정밀도 손실(loss of precision)

    항상 `문자열`을 반환! 그러므로 소수점 다음에 오는 숫자가 항상 2개가 될 수 있음에 주의. cf. `$0.30` 같은 값을 보여줄 때는 유용

    ```javascript
    let sum = 0.1 + 0.2;
    console.log( sum ); // 0.30000000000000004
    console.log( sum.toFixed(2) );
    // 0.30

    // 숫자형으로 강제 변환 ( 단항 덧셈 연산자 사용)
    console.log( +sum.toFixed(2) );
    // 0.3
    ```

### isNaN, isFinite

- **`isNaN(value)`**

    인수를 숫자로 변환한 다음 NaN인지 테스트

    NaN은 NaN 자기 자신을 포함하여 그 어떤 값과도 같지 않기 때문에 `isNaN(value)`함수가 필요

    ```javascript
    console.log( NaN === NaN ); // false       

    // 그러므로 함수를 활용해야 함
    console.log( isNaN(NaN) ); // true
    ```

- **`isFinite(value)`**

    인수를 숫자로 변환 후 변환한 숫자가 NaN/Infinity/-Infinity가 아닌 `일반 숫자`인 경우 true 반환

    ```javascript
    // 일반 숫자인 경우
    console.log( isFinite("500") ); // true      

    // NaN인 경우
    console.log( isFinite("string") ); // false

    // Infinity인 경우
    console.log( isFinite(Infinity) ); // false
    ```

    `문자열`이 일반 숫자인지 검증하는 데 사용

- `빈 문자열` or `공백만 있는 문자열`은 isFinite포함 모든 숫자 내장함수에서 `0`으로 취급

### parseInt, parseFloat

불가능할 때까지 문자열에서 숫자를 `'읽음'`

- **`parseInt()`**

    문자열을 **`정수`**로 반환

    `parseInt(str, radix)`에서 `radix`는 원하는 `진수` 지정

    소수점을 과감히 버리기 때문에 주의해야 하고, **정확한 결과 값을 원할 때**는 `radix` 인자를 **반드시** 전달할 것

    ```javascript
    // 문자열에서 숫자로 변환
    console.log( parseInt("200px") ); // 200
    // 진법을 지정했을 때(10진법)
    console.log( parseInt("010", 10) ); // 3

    // 지정하지 않았을 때( 0으로 시작하면 8진수로 인식 )
    console.log( parseInt("010") ); // 8
    ```

- **`parseInt()`**

    **`부동 소수점 숫자`**를 반환

    ```javascript
    console.log( parseFloat("31.45.3.4") ); // 31.45, 두번째 점에서 숫자 읽기 중지
    ```

### 그 외 : 내장객체 `Math`

- `Math.random()`

    `0 이상 1 미만`의 난수 반환

    `최대값`, `최소값`을 사용하여 범위 지정 가능

    ```javascript
    let num1 = Math.random();
    console.log(num1); // 0.1487797720982933

    // 범위 지정했을 경우
    let num2 =  Math.random() * 10;
    console.log(num2); // 5.316723490362653

    // 지정한 범위 내에서 정수값만 추출하고 싶을 때? - Math.floor 사용
    console.log( Math.floor(Math.random() * 10) ); // 6
    ```

- `Math.max(a, b, c...)` / `Math.min(a, b, c...)`

    인수 중 최대/최솟값 반환

    ```javascript
    console.log( Math.max(10, -2, 500, 0) ); // 500

    console.log( Math.min(10, -2, 500, 0) ); // -2
    ```

- `Math.pow(n,power)`

    n을 power번 `거듭제곱`한 값을 반환

    ```javascript
    console.log( Math.pow(2, 5)); // 32, 2의 5제곱
    ```

- `Math.floor()`

    주어진 숫자와 같거나 작은 `정수` 중 가장 큰 수 반환

### 추가 reference

- Javascript : 데이터 타입(Number, String, Boolean)

<https://velog.io/@canonmj/Javascript-%EB%8D%B0%EC%9D%B4%ED%84%B0-%ED%83%80%EC%9E%85-Number-String-Boolean>

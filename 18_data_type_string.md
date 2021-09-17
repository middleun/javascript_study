# 문자열

자바스크립트에서는 UTF-16을 이용해 문자열 인코딩

## 따옴표

### - 작은 따옴표, 큰 따옴표

### - 백틱( `` )

- `템플릿 리터럴(template literal)` 가능

    `&{...}`를 사용하여 표현식을 문자열 중간에 삽입

- 여러 줄 작성 가능

- 태그드 템플릿(tageed templates)

    템플릿 리터럴을 이용하여 `함수`의 인자를 파싱하여 넘겨줌

## 특수 기호

### 이스케이프 문자(escape character) `역슬래시( \ )`

- 문자열 내에 따옴표를 넣을 때

    `\'`, `\"`

    ```javascript
    // let str = 'kk's world';
    // 위와 같은 문제를 피하기 위해, \ 를 사용해 특수문자를 문자열 문자로 변환해줌
    let str = 'kk\'s world';
    console.log(str); // kk's world
    ```

- 줄 바꿈 문자

    `\n`

- 역슬래시

    `\\`

## 문자열의 길이

### `length` 프로퍼티

**NOT** function but property!

```javascript
let str1 = "hello"
let str2 = "kk\'s world"
console.log( str1.length ); // 5
console.log( str2.length ); // 10
```

## 특정 글자에 접근

문자열 내 **특정 위치**(pos : position)의 글자에 접근할 때,

### - 대괄호( `[]` ) 사용

### - str.`charAt(pos)`

문자열에서 지정한 위치의 `문자`를 반환

하위호환을 위해 남아있는 메소드. 대괄호를 더 많이 이용

### - str.`charCodeAt(pos)`

문자열에서 지정한 위치의 문자의 `unicode`를 반환

```javascript
let str = "Hello World!";

// 첫번째 글자 반환 
console.log( str[0] ); // H
console.log( str.charAt(0) ); // H

// 마지막 글자 반환
console.log( str[str.length - 1] ); // !
console.log( str.charAt(str.length - 1) ); // !

// 반환할 글자가 없을 때
console.log( str[100] ); // undefined
console.log( str.charAt(100) ); // ''(빈 문자열)
```

## 대소문자 변경

### - str.`toLowerCase()`

대문자를 소문자로 변경

### - str.`toUpperCase()`

소문자를 대문자로 변경

```javascript
// 소문자로
console.log( "hello".toUpperCase() ); // HELLO

// 대문자로
console.log( "HELLO".toLowerCase() ); // hello

// 글자 하나의 케이스 변경
console.log( "hello"[0]. toUpperCase() ); // H
```

## 부분 문자열(substring) 찾기

### - str.`indexOf(substr, pos)`

문자열(str) 내의 특정 위치(pos)에서부터 시작해서 부분 문자열(substr)이 **처음**으로 발견되는 위치(index)를 반환

원하는 부분 문자열을 찾으면 `위치`를 반환, 그렇지 않으면 `-1`을 반환

대소문자 구분

```javascript
let str = "manners maketh man";
let substr = "man";

console.log( str.indexOf(substr) ); // 0 ("manners"안의 "man")
console.log( str.indexOf(substr,2) ); // 15

// 대소문자 구분 
let str2 = "Manners maketh man";
let substr2 = "Man";

console.log( str2.indexOf(substr2) ); // 0
console.log( str2.indexOf(substr2,2) ); // -1, 대소문자를 따지므로 원하는 문자열을 찾지 못함 
```

### - str.`lastIndexOf(substr, pos)`

문자열 안에서 지정된 텍스트가 **마지막**으로 발견되는 위치 반환

## 문자열에서 문자열 탐색(searching)

### - `search()`

문자열 안에서 지정된 텍스트를 탐색하여 일치하는 곳의 위치를 반환

indexOf()와 같은 값을 반환하지만, 더 강력한 탐색 값을 취할 수 있음

## 부분 문자열 추출

### - str.`slice(start, end)`

- `start` 부터 `end` 까지(end 미포함)

- 음수 허용 ( 문자열의 끝에서부터 계수 )

### - str.`substring(start, end)`

- `start` 와 `end` 사이

- 음수 허용 X, 음수는 0 으로 취급

### - str.`substr(start, length)`

- `start` 부터 `length` 개의 글자

- 음수 허용

```javascript
let str = "Manners maketh man";

console.log( str.slice(0, 6) ); // Manner

console.log( str.slice(8) ); // maketh man

// 음수일 경우 끝에서부터 시작
console.log( str.slice( -2, -1) ); // a

```

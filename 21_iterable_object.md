# iterable 객체

## 반복 가능한 객체(iterable object) 또는 iterable

: `Symbol.iterator` 속성에 **특별한 형태의 함수**가 들어있는 객체

: 이 때 **해당 객체는 `iterable protocol`을 만족함**

```javascript
let arr = [1,2,3,4,5];
let test = arr[Symbol.iterator]();

console.log(test); // Array Iterator {}
```

## iterable 객체를 만들어내는 생성자

- `String`

- `Array`

- `TypedArray`

- `Map`

- `Set`

이 중에서도 문자열(String)과 배열(Array)는 가장 광범위하게 쓰이는 내장 이터러블

```javascript
// 'for...of' ex
// for...of는 문자열의 각 글자를 순환
for (let char of "test") {
    // 글자 하나당 한 번 실행 
    console.log( char ); // t // e // s // t 한 번씩 차례대로 출력
}
```

## iterable의 사용

- for...of 반복문

- spread 연산자 (...)

- 분해대입

## iterator 객체

: iterator protocol을 따르는 객체

: 즉, 항상 `next()`라는 메소드를 가지며, 이 메소드는 `value`, `done` 속성을 가진 객체를 반환한다는 의미

```javascript
let arr = [1,2,3,4,5];
let test = arr[Symbol.iterator]();

console.log(test); // Array Iterator {}

console.log(test.next()); // {value: 1, done: false}
console.log(test.next()); // {value: 2, done: false}
console.log(test.next()); // {value: 3, done: false}
console.log(test.next()); // {value: 4, done: false}
console.log(test.next()); // {value: 5, done: false}
console.log(test.next()); // {value: undefined, done: true} - 순서상 값이 존재하지 않으면 true
```

## 요약 정리

1. **iterable** 객체는 **iterable protocol**을 만족한다

    즉, `Symbol.iterator` 속성에 **특정 형태의 함수**가 저장되어 있다

2. 이 때, Symbol.iterator 속성에 저장되어 있는 함수는 **iterator** 객체를 반환해야 한다

3. iterator객체는 아래의 조건을 만족해야 한다

    - **next**라는 메소드를 가짐

    - next메소드는 다음 두 속성을 갖는 객체를 반환

        - `value` : 현재 순서의 값

        - `done` : 반복이 모두 끝났는지

### 추가 reference

Iterable | Javascript로 만나는 세상

<https://helloworldjavascript.net/pages/260-iteration.html>

[JavaScript] iterable, iterator

<https://jongbeom-dev.tistory.com/139>

# 배열(Array)

순서가 있는 컬렉션을 저장할 때 쓰는 자료구조

## 배열 선언

```javascript
// 빈 배열 만들기
let arr = new Array();
let arr = []; // 대부분 이 방법으로 배열 선언 

// 초기 요소 넣는 것도 가능 
let colors = ["black", "red", "white", "blue", "green"];
```

## 인덱스(index)

배열 내 순서를 나타냄, 0부터 시작

```javascript
let colors = ["black", "red", "white", "blue", "green"];

// 특정요소 불러내기
console.log( colors[1] ); // red

// 특정요소 수정
colors[1] = "yellow";
console.log(colors); // (5) ['black', 'yellow', 'white', 'blue', 'green']

// 새로운 요소 추가
colors[5] = "red";
alert(colors); // black,yellow,white,blue,green,red
```

## length

배열의 길이, 정확히는 `(인덱스 중 가장 큰 값) + 1`

배열 메서드는 length 프로퍼티를 자동으로 조정

## 배열을 데큐(deque)처럼 사용하기

### 데큐(deque, Double Ended Queue))

: 처음이나 끝에 요소를 더하거나 빼주는 연산을 제공하는 자료구조

### pop()

배열 `끝` 요소를 제거하고, 제거한 요소를 반환

```javascript
let colors = ["black", "red", "white", "blue", "green"];

console.log(colors.pop()); // green - 배열 끝에서 "green" 제거, 제거한 요소 반환

alert(colors) // black,red,white,blue
```

### push(...items)

`items`를 배열 `끝`에 추가

```javascript
let colors = ["black", "red", "white", "blue", "green"];

colors.push("yellow");

alert(colors) // black,red,white,blue, green, yellow
```

### shift()

배열 `처음` 요소를 제거하고, 제거한 요소를 반환

```javascript
let colors = ["black", "red", "white", "blue", "green"];

console.log(colors.shift()); // black - 배열 끝에서 "black" 제거, 제거한 요소 반환

alert(colors); // red,white,blue,green
```

### unshift(...items)

`items`를 배열 `처음`에 추가

```javascript
let colors = ["black", "red", "white", "blue", "green"];

colors.unshift("yellow");

alert(colors) // yellow, black,red,white,blue, green
```

### push와 unshift는 요소 여러 개 한 번에 추가 가능

### 실행속도 비교

: `push`나 `pop` **>** `shift`나 `unshift`

- 배열 `앞`에 무언가를 해주는 메소드

    인덱스가 0인 요소를 제거 -> 모든 요소를 왼쪽으로 이동-> length 프로퍼티 값 갱신

- 배열 `끝`에 무언가를 해주는 메소드

    배열 긑 요소를 제거 -> length 프로퍼티 값 갱신, 즉 **요소 이동 필요 X**

## 반복문

### for

`for(let i = 0; i<arr.length; i++)`

: 배열을 순회할 때 쓰는 가장 빠르고 오래된 방법, 인덱스 사용

```javascript
let colors = ["black", "red", "white", "blue", "green"];

for (let i = 0; i < colors.length; i++) {
    console.log( colors[i] ); // black // red // white // blue // green
}
```

### for..of

`for(let item of arr)`

: 배열 요소에만 사용되는 모던한 문법

: 현재 요소의 인덱스는 얻을 수 없고 값만 얻을 수 있음

```javascript
let colors = ["black", "red", "white", "blue", "green"];

for (color of colors) {
    console.log( color ); // black // red // white // blue // green
}
```

### for..in

`for(let i in arr)`

: `객체`에 최적화된 반복문, 모든 프로퍼티를 대상으로 순회하기 때문에 **'필요없는'** 프로퍼티들이 문제를 일으킬 가능성이 있음 => 배열엔 사용하지 않는 것이 좋음

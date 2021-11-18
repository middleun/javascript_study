# 구조 분해 할당(Destructuring Assignment)

> 구조분해할당 구문은 배열이나 객체의 속성을 `해체`하여 그 값을 **개별 변수**에 담을 수 있게 하는 Javascript 표현식입니다 - [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment)

즉, obj나 array로 구조화된 변수를 분해 or 할당이 가능!

함수의 매개변수가 많거나 매개변수 기본값이 필요한 경우 유용

## 배열 구조 분해

```javascript
const arr = ["Bora", "Lee"];

// 구조분해할당을 이용해 firstName - arr[0], surName - arr[1] 할당
const [firstName, surName] = arr;

console.log(firstName); // Bora
console.log(surName); // Lee
// 인덱스 이용할 필요 X
```

## 기본값

변수에 **기본값**을 할당하면 분해한 값이 `undefined`일 때 그 값을 대신 사용

```javascript
let a, b;

[a = 1, b = 3] = [1]; 

console.log(a); // 1
console.log(b); // 3 (분해한 b의 값이 undefined이므로 기본값을 대신 사용)
```

### 변수 값 교환

```javascript
let a = 1;
let b = 3;
[a, b] = [b, a];
console.log(a); // 3
console.log(b); // 1

// 
let guest = "Jane";
let admin = "Pete";

[guest, admin] = [admin, guest];

console.log(`admin : ${admin}, guest : ${guest}`);
```

## 객체 구조 분해

```javascript
const girl = {
    name: "Bora",
    age: "10",
    country: "Korea",
};

// 구조분해할당이 없이는 이런 식으로 하나하나 지정했어야 함
const name = girl.name;
const age = girl.age;

// 구조분해할당을 이용하면?
const {name, age, country} = girl;
console.log(name); // Bora
console.log(age); // 10
```

### 새로운 변수 이름으로 할당

객체로부터 속성을 해체하여 객체의 원래 속성명과는 다른 이름의 변수에 할당할 수 있음

```javascript
let options = {
    title: "Navigation",
    width: 100,
    height: 200
};

// {객체 프로퍼티 : 목표 변수}로 새롭게 할당
// 즉, width는 w로, height는 h로, title은 tit로 할당
// 순서 바뀌어도 ok
let {width:w, height:h, title: tit} = options;

console.log(w); // 100
console.log(h); // 200
console.log(tit); // Navigation
```

### 기본값

객체로부터 해체된 값이 undefinde인 경우, 변수에 기본값 할당 가능(배열일 경우와 마찬가지로 적용)

```javascript
let {a = 10, b = 5} = {a: 3};

console.log(a); // 3
console.log(b); // 5 (객체로부터 분해된 b의 값이 undefined 이므로, 기본값인 5를 대신 할당)
```

### 기본값 갖는 새로운 이름의 변수에 할당

`새로운 변수명` 할당과 `기본값` 할당 동시에 가능

```javascript
let {a: aa = 10, b: bb = 5} = {a: 3};

console.log(aa); // 3
console.log(bb); // 5 (객체로부터 분해된 b의 값이 undefined 이므로, 기본값인 5를 새로운 변수명 bb에 할당)
```

## 중첩 구조 분해

객체나 배열이 다른 객체나 배열을 포함하는 경우, 좀 더 세밀한 패턴을 사용해서 중첩 배열과 객체의 정보를 추출

```javascript
let user = {
    name: {
        firstName: "Bora",
        lastName: "Lee",
    },
    items: ["phone", "desktop"],
};

let {
    id = "guest", // 분해하려는 객체에 id 프로퍼티가 없으므로 기본값 설정
    name: {
        firstName,
        lastName,
    },
    items: [item1, item2],
} = user;

// -> 객체의 모든 프로퍼티를 상응하는 변수에 할당
console.log(id); // guest
console.log(firstName); // Bora
console.log(item1); // phone
```

## 변수에 배열/객체의 나머지 할당

배열/객체 앞쪽의 값 몇 개만 필요하고 나머지 값은 한 번에 모아서 저장하고 싶을 때, `...`를 이용하여 매개변수 하나에 할당

```javascript
// 배열
let [name1, name2, ...rest] = ["Jane", "Pete", "Kate", "KK"];

console.log(name1); // Jane
console.log(rest); // (2) ['Kate', 'KK']
console.log(rest[1]); // KK

// 객체
let options = {
    title: "Navigation",
    height: 200,
    width: 100,
};

let {title, ...rest} = options; // title 외의 프로퍼티를 '나머지'로 할당

console.log(title); // Navigation
console.log(rest.height); // 200
console.log(rest.width); // 100
```

### 기타 reference

- [[JSInfo]구조 분해 할당](https://velog.io/@cptkuk91/JSInfo19)

- [<자바스크립트> 구조 분해 할당](https://haesoo9410.tistory.com/187)

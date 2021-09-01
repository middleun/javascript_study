# 참조에 의한 객체 복사

- 원시타입 : '값 그대로' 저장, 할당, 복사

- 객체 : '참조에 의해(by reference)' 저장, 복사

객체 자체가 저장되는 것이 아니라 객체가 저장되어 있는 '메모리 주소', 즉 `객체에 대한 '참조값'`이 저장됨

```javascript
// 원시형
let a = 1;
let b = a;
b = 2;
console.log(a) // 1 

// 객체
let a= { id : 1 }; // 생성된 객체를 '가리키는' 참조값을 저장하고 있음
let b = a;  
console.log(a.id); // 1
console.log(b.id); // 1 
// 두 변수 모두에 동일 객체에 대한 참조값이 저장되었으므로 동일한 결괏값 출력

b.id = 2; // so, 프로퍼티값을 갱신해도 출력값이 동일
console.log(a.id) // 2
console.log(b).id) // 2
```

## 참조에 의한 비교

객체 비교시 동등연산자( == )와 일치연산자( === ) 동일하게 동작

`피연산자인 두 객체가 동일한 객체인 경우 일치, 동등 비교 모두에서 참을 반환`

```javascript
let a = {};
let b = a; // 참조에 의한 복사 / 같은 객체를 참조 

console.log( a == b ); // true
console.log( a === b ); // true

// 
let a = {};
let b = {}; 

// 비어있는 객체여도 각각 독립된 객체이므로 !a == b
console.log( a == b ); // false
```

## 객체 복사, 병합과 Object.assign

객체가 할당된 변수를 복사하는 것은 참조에 의한 복사!

객체를 복제하고 싶다면?

- 새로운 빈 객체 생성 후 기존 객체의 프로퍼티 전부를 복사

```javascript
let user = {
    id : 1,
    name : "Ann"
};

// 새로운 빈 객체 생성 
let cloneUser = {};

// 기존 객체의 프로퍼티 순회 (for...in) 후 기존 객체 프로퍼티 전부 복사 
for (let key in user) {
    cloneUser[key] = user[key];
}

```

- `Object.assign` 사용

`얕은 복사(Shallow copy)`

`Object.assign(target, [src1, src2, src3...])`

`target`
: 목표 객체

`src1,....,srcN`
: 출처 객체, 즉 복사하고자 하는 객체

객체 src1, ...., srcN의 프로퍼티를 target에 복사

```javascript
let user = {
    id: 1,
    name: "Ann"
};

let addProperty1 = { age: 20 };
let addProperty2 = { gender: "female" };

// Object.assign 사용하여 addProperty1과 addProperty2의 프로퍼티 복사 
Object.assign(user, addProperty1, addProperty2);
console.log(user); // {id: 1, name: "Ann", age: "20", gender: "female"}
```

```javascript
// 목표 객체에 동일한 이름을 가진 프로퍼티가 있으면 기존 값에 덮어씌움
let user = {
    id: 1,
    name: "Ann"
};

let addProperty = { name : "Jack" };

Object.assign(user, addProperty1);
console.log(user); // {id: 1, name: "Jack"}

// 빈 객체 생성, 반복문 사용없이도 간단하게 객체 복사
let cloneUser = Object.assign({}, user);
console.log(cloneUser); // {id: 1, name: "Ann"}
```

얕은 복사는 중첩 객체를 처리하지 못함

## 중첩객체 복사 

`깊은 복사(Deep copy)`

- sturctured clone algorithm

user[key]의 각 값을 검사하면서 그 값이 객체인 경우 객체의 구조도 복사해주는 `반복문(for...in)` 사용

복사를 진행하다가 객체를 만나면 함수를 재귀적으로 진행 

```javascript
let user = {
    name: "Ann",
    age: "20",
    grade:{
        speaking: "A+",
        grammer: "B",
        reading: "B+"
    },
};    

function copyObj(obj){
    const result = {};

    for (let key in obj) {
        if (typeof obj[key] === 'object') {
            result[key] = copyObj(obj[key]);
        } else {
            result[key] = obj[key];
        }
    }
    return result;
}

const copiedUser = copyObj(user);
copiedUser.name = "John";
copiedUser.grade.speaking = "A";
console.log(copiedUser); //{name: "John", age: "20", grade: {…}}
console.log(user.grade.speaking === copiedUser.grade.speaking); //false
```

- `JSON.stringify()` 와 `JSON.parse()`사용

`JSON.stringify()` : 객체를 json 문자열로 변환

`JSON.parse()` : json 문자열을 객체로 변환

JSON.stringify()를 이용해 json 문자열로 변환하는 과정에서 원본 객체와의 참조가 끊어지기 때문에 JSON.parse()를 이용해 다시 객체로 변환 

다른 방법에 비해 느리고, `Date`나 `함수`, `undefined`, `regExp`, `infinity`가 객체 내에 존재할 경우에는 원하는 결과를 얻을 수 없음

```javascript
let user = {
    name: "Ann",
    age: "20",
    grade:{
        speaking: "A+",
        grammer: "B",
        reading: "B+"
    },
};

const copiedUser = JSON.parse(JSON.stringify(user));
copiedUser.name = "John";
copiedUser.grade.speaking = "A";
console.log(copiedUser); //{name: "John", age: "20", grade: {…}}
console.log(user.grade.speaking === copiedUser.grade.speaking); //false
```

- lodash의 메서드 `_.cloneDeep(obj)`사용

`lodash` : 자바스크립트 고차함수 집합 및 함수형 라이브러리

array, collection, date 등 데이터의 필수적인 구조를 쉽게 다룰 수 있게끔 하는데에 사용

`_.cloneDeep(obj)` : `_.clone`을 재귀적으로 수행해주는 함수

```javascript
let user = {
    name: "Ann",
    age: "20",
    grade:{
        speaking: "A+",
        grammer: "B",
        reading: "B+"
    },
};

const copiedUser = _.cloneDeep(User);
copiedUser.name = "John";
copiedUser.grade.speaking = "A";
console.log(copiedUser); //{name: "John", age: "20", grade: {…}}
console.log(user.grade.speaking === copiedUser.grade.speaking); //false
```

- 추가 reference

자바스크립트 참조 타입(객체)

<https://velog.io/@smp2103/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%B0%B8%EC%A1%B0-%ED%83%80%EC%9E%85%EA%B0%9D%EC%B2%B4>

생활코딩 유튜브

<https://www.youtube.com/watch?v=dOTpbvvOV0M&ab_channel=%EC%83%9D%ED%99%9C%EC%BD%94%EB%94%A9>

[javascript] 얕은 복사, 깊은 복사

<https://velog.io/@th0566/Javascript-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%AC-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%AC>

JavaScript로 Deep Copy 하는 여러 방법

<https://leonkong.cc/posts/js-deep-copy.html>

Javascript | 얕은 복사와 깊은 복사(Part.1)
<https://velog.io/@shin6403/Javascript-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%AC%EC%99%80-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%ACPart.1>
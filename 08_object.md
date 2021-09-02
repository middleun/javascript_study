# 객체 : 기본 (Object)

원시형(primitive type)과 달리 키로 구분된 데이터 집합이나 복잡한 개체 등 다양한 데이터 저장 가능

빈 객체 생성

```javascript
let movie = new Object(); // '객체 생성자(object constructor)' 문법
let movie = {}; // '객체 리터럴(object literal)' 문법
```

`{ key : value }`

프로퍼티 값에는 어떤 표현식도 올 수 있음

이 값이 함수 일 경우, 프로퍼티 -> `메서드`

```javascript
let movie = {
    title : "Black Widow",
    genre : "action",
    year : "2021", 
};
```

프로퍼티 접근

- 점 표기법 : `obj.property`

- 대괄호 표기법 : `obj["property"]`

프로퍼티 삭제

 `delete obj.property`

## 프로퍼티 존재 여부 확인

- 일치연산자와 undefined 사용

```javascript
let movie = {
    title : "Black Widow",
    genre : "action",
    year : "2021", 
};

alert( movie.detail === undefined ) //true : 프로퍼티가 존재하지 않음
```

대부분의 경우에는 이 방법이 잘 작동하지만, 프로퍼티는 존재하는데 undefined가 값에 할당된 경우에는 존재 여부 판단이 어려움
-> in 연산자 사용

- in 사용
`"key" in object`

```javascript
let movie = {
    title : "Black Widow",
    genre : "action",
    year : "2021", 
};

alert( "title" in movie ) //true : movie.title이 존재 
alert( "detail" in movie ) // false : movie.detail은 존재X 
```

## 'for...in' 반복문

객체의 모든 키를 순회할 수 있음

```javascript
for (key in object) {
    // 각 프로퍼티 key를 이용하여 본문 실행
};
```

```javascript
let movie = {
    title : "Black Widow",
    genre : "action",
    year : "2021", 
};

for (let data in movie) {

    alert( data ); // key - title, genre, year 
    alert( movie[data] ) // value - Black Widow, action, 2021
}
```

## 객체 정렬 방식

정수 프로퍼티(integer property)는 자동 정렬, 그 외 프로퍼티는 객체에 추가한 순서대로 정렬

```javascript
//Q1
// 빈 객체 user 만들기
let user = {};
// user에 키가 name, 값이 John인 프로퍼티 추가
user.name = "John";
// user에 키가 surname, 값이 Smith인 프로퍼티 추가 
user.surname = "Smith";
// name의 값을 Pete로 수정
user.name = "Pete"
//user에서 프로퍼티 name 삭제 
delete user.name;

//Q2 *
// 객체에 프로퍼티가 하나도 없는 경우 true, 그렇지 않은 경우 false 반환하는 함수 isEmpty(obj) 생성

function isEmpty(obj) {
    for (let key in obj){
        return false;
    } 
    return true;
}

//Q3 프로퍼티 합계 
let salaries = {
    John : 100,
    Ann : 160,
    Pete : 130
}

let sum = 0;
for (let key in salaries){
    //sum += salaries.key -> Nan
    sum += salaries[key]; //390
}

//Q4 프로퍼티 값 두 배로
// obj의 프로퍼티 값이 숫자인 경우 그 값을 두 배 해주는 함수 multiplyNumeric(obj)

function multiplyNumeric(obj){
    if (typeof obj[key] === 'number'){
        obj[key] *= 2;
    }
}

// ↓ / for...in 반복문 사용!
function multiplayNumeric(obj){
    for (let key in obj){
        if (typeof obj[key] == 'number'){
            obj[key] *= 2;
        }
    }
}
```

- reference

<https://velog.io/@smp2103/%EC%9E%90%EB%B0%94%EC%8A%A4%ED%81%AC%EB%A6%BD%ED%8A%B8-%EC%B0%B8%EC%A1%B0-%ED%83%80%EC%9E%85%EA%B0%9D%EC%B2%B4>

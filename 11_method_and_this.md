# 메소드(method)와 this

## 메소드(method)

객체 프로퍼티에 저장된 함수

```javascript
let user = {
    name: "Ann",
    age: "20",
    grade:{
        speaking: "A+",
        grammer: "B",
        reading: "B+"
    }
};

function sayHello(){
    alert("Hello!");
};

user.sayHello = sayHello;

user.sayHello(); // Hello!
```

## this

javascript에서는 모든 함수에 this 사용 가능, this의 값이 결정되어 있지 않고 문맥에 따라 그 값이 바뀜

**런타임에 결정** : 메소드가 어디서 정의되었는지에 상관없이 '점 앞의' 객체가 무엇인가에 따라 결정됨

>대부분의 경우 this의 값은 함수를 호출한 방법에 의해 결정됩니다. 실행중에는 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있습니다. - [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)

- 화살표 함수는 자신만의 this를 가지지 않음

    so, 화살표 함수 내부에서 this사용 -> 외부에서 값을 가져옴

### 전역 범위(Global Context)

일반적으로 `this`를 호출하면 `window`라는 전역 개체를 가리킴(Node.js에서는 Global)

```javascript
// 전역범위 호출 
console.log(this); //window {}
```

### 단순 함수 호출

this의 값이 호출에 의해 설정되지 않으므로 window 전역 객체를 기본값으로 참조

```javascript
// 단순 함수 호출
function sayHello() {
    console.log(this); // this - window

    // 함수 안에 함수가 선언된 내부 함수 호출
    function askName() {
        console.log(this); // this - window
    }
    askName();
}
sayHello();
```

### 객체의 메소드(Method)

- 객체나 클래스 내부에 메소드 함수를 선언하는 경우

>함수를 어떤 객체의 메소드로 호출하면 this의 값은 그 객체를 사용합니다. - [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)

```javascript
// 객체 또는 클래스 안에서 메소드 실행할 때 this는 object를 가리킴
let user = {
    name: "Ann",
    age: "20",
    sayHello: function(){
        console.log("hello" + this.name); // 여기서 this는 객체인 user를 가리키는 것
    }
}
user.sayHello(); // hello Ann
```

- 함수를 객체 외부에 선언하고 객체 안에서 호출하는 경우

```javascript
let user = {
    name: "Ann",
    age: "20",
    sayHello: function(){
        console.log("hello" + this.name); // 여기서 this는 객체인 user를 가리키는 것
    }
}

// 일반 함수 showGreeting을 객체 외부에 선언
function greeting(){
    // 아직까지는 this가 전역 객체 window
    console.log("happy " + this.name + "'s day");
}

// usr 객체의 greeting속성에 일반 함수 showGreeting 추가
user.greeting = greeting;

user.greeting(); // 해당 user 객체 안에서 호출 -> happy Ann's day
```

### 추가 reference

JavaScript 개발자라면 꼭 알아야 할 this

<https://wormwlrm.github.io/2019/03/04/You-should-know-JavaScript-this.html>

코딩앙마 유튜브

<https://www.youtube.com/watch?v=KF6t61yuPCY&ab_channel=%EC%BD%94%EB%94%A9%EC%95%99%EB%A7%88>

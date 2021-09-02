# 메서드(method)와 this

## 메서드(method)

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

메서드 내부에서 this 키워드를 사용하여 객체에 접근

```javascript
let user = {
    name: "Ann",
    age: "20",
    
    sayHello(){
        alert(this.name); // this : 현재 객체
    }
};

user.sayHello(); // Ann
```

javascript에서는 모든 함수에 this 사용 가능

런타임에 결정 : 메서드가 어디서 정의되었는지에 상관없이 '점 앞의' 객체가 무엇인가에 따라 결정됨

>대부분의 경우 this의 값은 함수를 호출한 방법에 의해 결정됩니다. 실행중에는 할당으로 설정할 수 없고 함수를 호출할 때 마다 다를 수 있습니다.

- [mdn](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/this)

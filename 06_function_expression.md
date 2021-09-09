# 함수표현식(Function Expression)

함수를 생성하고 함수를 변수에 할당

```javascript
//함수 선언, 변수 getName에 저장
function getName(){
    prompt("who are you?", "");
}

// getName을 새로운 변수 func에 복사
let copyFunc = getName; // cf.getName(); 할 경우 함수의 반환값이 저장됨!

//복사한 함수 or
copyFunc(); 
// 본래 함수로 함수 호출 가능
getName(); 
```

함수표현식으로 정의하면?

```javascript
let getName = function(){
    prompt("who are you?","");
};

let func = getName;
```

## 콜백함수

함수를 함수의 인수로 전달하고 필요하다면 그 함수를 나중에 `호출`

```javascript
//ex1
function ask(question, yes, no){
  if(confirm(question)) yes()
  else no();
}

function deleteCon(){
  alert("삭제하겠습니다");
}

function letGoCon(){
  alert("취소하겠습니다");
}

//question의 답변에 따라 deleteCon과 legGoCon이 각각 ask함수의 인수로 전달 
ask("정말로 삭제하시겠습니까?", deleteCon, letGoCon)

//ex2
function showGreeting(name){
  alert("Hello," + name);
}

function getName(ask){
  let value = prompt("what is your name?");
  ask(value);
}

getName(showGreeting);
```

## 함수표현식 vs 함수선언문

### 문법

- 함수표현식 : 표현식이나 구문 구성 내부에 생성, `표현식의 일부`로 존재

- 함수선언문 : 주요 코드 흐름 속 `독립된 구문 형태`로 존재

### 함수를 생성하는 시점

- 함수표현식 : 실제 실행 흐름이 `함수에 도달했을 때`

함수가 선언되기 전까지 접근 불가

- 함수선언문 : 함수 선언문이 `정의되기 전에도` 호출 가능(호이스팅)

스크립트 실행 전 `준비단계`에서 선언된 함수 선언문을 찾아 함수 생성

### 스코프

- use trict 내에서 함수 선언문은 선언된 코드블록 안에서만 유효,

블록 밖에서는 함수에 접근 불가

- but, 함수표현식 사용하면 코드블록 밖에서도 접근 가능

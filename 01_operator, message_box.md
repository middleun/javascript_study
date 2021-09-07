# 연산자(Operator), 대화상자

## 증감연산자

1. **증가연산자(++)**

```javascript
    // 후위 연산 
    let counter = 2;
    // 뒤에 ++를 넣으면 "증가시키기 전"의 값을 변수에 할당
    let result = counter++;
    console.log(result); // 2
```

```javascript
    // 전위 연산
    let counter = 2;
    // 앞에 ++를 넣으면 "증가시킨" 값을 변수에 할당
    let result = ++counter;
    console.log(result); // 3
```

## 비교연산자

`문자열 비교`

: 문자열의 첫번째 글자부터 마지막 글자까지 한 글자씩 비교

한 글자씩 비교가 끝난 후 문자열의 길이가 다르다면 길이가 더 긴 것을 "크다"고 결론

1. **`동등 연산자 ( == )`**

    형이 다른 피연산자를 비교할 때 피연산자를 숫자형으로 바꾸기 때문에(`자동형변환`) 자료형이 달라도 동등한 것으로 인식

    ```javascript
    console.log("01" == 1); // true

    console.log(0 == false); // true
    ```

2. **`일치 연산자 ( === )`**

    자료형의 동등여부까지 검사해서 형이 일치해야 일치한 것으로 인식

    동등 연산자( == )의 엄격한 버전

    ```javascript
        console.log("01" === 1); // false

        console.log(0 === false); // false

        console.log("5" > "10"); // true , 문자열의 비교는 사전순("5"와 "1"을 먼저 비교)
    ```

## 대화상자(message boxes)

### alert

메시지를 `보여줌`

`alert("contents");`

### prompt

`입력` 받음

`result = prompt(title, [default]);`

`title` : 사용자에게 보여줄 문자열

`default` : 입력 필드의 초깃값(선택값)

### confirm

`확인` 받음

`result = confirm(question);`

```javascript
    // Q1
    let test = prompt("Test", '')
    console.dir(test)

    const body = document.querySelector("body");
    const userName = prompt("이름을 입력해주세요");
    console.log(userName);

    const nameCon = document.createElement("div");
    nameCon.innerHTML = userName;
    // console.log(nameCon);
    nameCon.style.color = "#000";
    nameCon.style.fontSize = "20px";
    body.appendChild(nameCon);
```

## 추가 / 형 변환

prompt로 입력받은 데이터 => 문자형

so, prompt로 입력받은 값으로 연산을 해야하는 경우, `Number()`로 `명시적 형변환`을 해줘야 함

### 추가 reference

코딩앙마 유튜브

<https://www.youtube.com/watch?v=KF6t61yuPCY&ab_channel=%EC%BD%94%EB%94%A9%EC%95%99%EB%A7%88>

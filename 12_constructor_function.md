# 생성자함수(Constructor Function)

1. 함수 이름의 첫 글자는 대문자로 시작

2. `new`연산자를 붙여 실행

`new operator`

사용자 정의 객체 타입 또는 내장 객체 타입의 인스턴스를 생성하는 연산자

```javascript
function Movie(title, genre, year){
    // this = {} - 빈 객체를 만들어 this에 할당
    this.title = title;
    this.genre = genre;
    this.year = year;
    this.user = function (user) {
        console.log(`${genre}를 선호하는 ${user} 님에게 영화 ${title}을(를) 추천드립니다`);
    } // 함수 본문 실행, this에 새로운 프로퍼티 추가해 this를 수정
    // return this;  - this 반환
}

const movie1 = new Movie("Coda", "drama", 2021)
// 새로운 객체에서 this가 가리키는 것 -> Movie1
const movie2 = new Movie("Free Guy", "sci-fi", 2021)
console.log(movie1); // Movie {name: "Coda", genre: "drama", year: 2021, user: ƒ}
movie1.user("Jane"); // drama를 선호하는 Jane 님에게 영화 Coda을(를) 추천드립니다
movie2.user("Levy"); // sci-fi를 선호하는 Levy 님에게 영화 Free Guy을(를) 추천드립니다
```

```javascript
function Calculator(read, sum, mul){
    this.read = function() {
        this.num1 = +prompt("숫자를 입력하세요", 0);
        this.num2 = +prompt("숫자를 하나 더 입력하세요", 0);
    }
    this.sum = function(){
        return this.num1 + this.num2;
    }
    this.mul = function(){
        return this.num1 * this.num2;
    }
}
let calculator = new Calculator();
calculator.read();

console.log("Sum= " + calculator.sum());
console.log("Mul= " + calculator.mul());
```

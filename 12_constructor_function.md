# 생성자함수(Constructor Function)

1. 함수 이름의 첫 글자는 대문자로 시작

2. `new`연산자를 붙여 실행

```javascript
function Movie(title, genre, year){
    this.name = title;
    this.genre = genre;
    this.year = year;
    this.user = function (user) {
        console.log(`${genre}를 좋아하는 ${user} 님에게 영화 ${title}을(를) 추천드립니다`);
    }
}

const movie = new Movie("Coda", "drama", 2021)
// 새로운 객체에서 this가 가리키는 것 -> movie
console.log(movie); // Movie {name: "Coda", genre: "drama", year: 2021, user: ƒ}
movie.user("Jane"); // drama를 좋아하는 Jane 님에게 영화 Coda을(를) 추천드립니다
```

빈 객체를 만들어 this에 할당

함수 본문 실행, this에 새로운 프로퍼티 추가해 this를 수정

this 반환

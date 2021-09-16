# 자료형 +

## 원시값의 메소드

### 원시 래퍼 객체(object wrapper)

원시값이 메소드나 프로퍼티에 접근하려 하면 추가 기능을 제공해주는 특수한 객체. 곧 삭제됨

- 문자열 메소드 대표적인 예 `str.toUpperCase()`
    인수로 받은 문자열의 모든 글자를 대문자로 바꿔줌

    ```javascript
    let str = "Welcome"; // 1. str은 원시값
    console.log( str.toUpperCase() ); // WELCOME
    // 2. 원시값의 프로퍼티(toUpperCase)에 접근하는 순간 특별한 객체가 생성됨.
    // 3. 메서드 실해, 새로운 문자열 반환
    // 4. 특별한 객체 삭제, 원시값 str만 남음
    ```

- 숫자열 메소드 대표적인 예 `toFixed(n)`
    원하는 자리에서 소수점 아래 숫자를 반올림

    ```javascript
    let pi = 3.141592;
    console.log( pi.toFixed(2) ); // 3.14
    ```

- `null/undefined`는 메소드가 없음
    래퍼 객체 X, 메소드도 제공 X

```javascript
// Q1
let str = "Welcome";

str.test = 5;
console.log(str.test); // undefined 
```

**- 원시값은 추가 데이터를 저장할 수 없음!**

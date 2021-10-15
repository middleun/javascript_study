# Kata in Codewars

## Sort and Star ~~(-ing)~~ ( 8kyu )

> You will be given a vector of strings. You must sort it **`alphabetically`** (case-sensitive, and based on the ASCII values of the chars) and then return the **`first value`**.
>
> The returned value must be a **`string`**, and have `"***"` `between each of its letters`.
>
> You should **not remove or add** elements from/to the array.

```javascript
// my solution
function twoSort(s) {
    // 배열 알파벳순으로 정렬(sort) 후 첫 번째 요소(splice) 반환, 배열을 문자열로 변환(join) 
    let result = s.sort().splice(0,1).join();
    // 단일 문자로 분리(split) 후, 결합문자("***") 사용해 다시 문자열 변환(join)
    return result.split("").join("***");
}

let arr1 = ["bitcoin", "take", "over", "the", "world", "maybe", "who", "knows", "perhaps"];
let arr2 = ["truns", "out", "random", "test", "cases", "are", "easier", "than", "writing", "out", "basic", "ones"];
twoSort(arr1); // 'b***i***t***c***o***i***n'
twoSort(arr2); // 'a***r***e'
```

```javascript
// Best solution of others
function twoSort(s) {
  return s.sort()[0].split('').join('***');
} // 인덱스를 사용하면 되었을 것을..!!! 복잡하게 돌고 돌아갔다

let arr1 = ["bitcoin", "take", "over", "the", "world", "maybe", "who", "knows", "perhaps"];
let arr2 = ["truns", "out", "random", "test", "cases", "are", "easier", "than", "writing", "out", "basic", "ones"];
twoSort(arr1); // 'b***i***t***c***o***i***n'
twoSort(arr2); // 'a***r***e'
```

## Replace With Alphabet Position ( 6kyu )

> In this kata you are required to, given a string, **replace** every letter with its **position** in the `alphabet`.
>
> If anything in the text isn't a letter, ignore it and don't return it.
>
> "a" = 1, "b" = 2, etc.

```javascript
function alphabetPosition(text) {
  let result = [];
  let alphabet = "abcdefghijklmnopqrstuvwxyz";
  
  for (let i = 0; i<text.length; i++) {
    let char = text[i].toLowerCase();
    //indexOf - 요소 발견하지 못하면 -1 반환
    if(alphabet.indexOf(char) !== -1) { 
      result.push(alphabet.indexOf(char) + 1);
    }
  }
  return result.join(" ");
}
alphabetPosition("The sunset sets at twelve o' clock."); // '20 8 5 19 21 14 19 20 5 19 5 20 19 1 20 20 23 5 12 22 5 15 3 12 15 3 11'
alphabetPosition(",m!fq=3/"); // '13 6 17'
```

## Unique In Order

> Implement the function unique_in_order which takes as argument a sequence and returns a list of items **without any elements with the same value** next to each other and preserving the original order of elements.

```javascript
// my solution - 1st try
var uniqueInOrder=function(iterable){
  let result  = [];
    for(char of iterable){
      if(!result.includes(char)) {
        result.push(char);
      }
    }
  return result;
  console.log(result); 
}
uniqueInOrder("AAAABBBCCDAABBB"); // (4) ['A', 'B', 'C', 'D']

// my solution - 2nd try
var uniqueInOrder=function(iterable){
  //your code here - remember iterable can be a string or an array
  let result  = [];
    for(let i = 0; i<iterable.length; i++) {
      if(iterable[i] === iterable[i+1]) {
        continue;
      } else {
        result.push(iterable[i]);
      }
    }
  return result;
  console.log(result);
}
uniqueInOrder("AAAABBBCCDAABBB"); // (6) ['A', 'B', 'C', 'D', 'A', 'B']
```

```javascript
// Best solution of others
function uniqueInOrder(it) {
  var result = []
  var last
  
  for (var i = 0; i < it.length; i++) {
    if (it[i] !== last) {
      result.push(last = it[i])
    }
  }
  
  return result;
}
```

## Flatten and sort an array (-ing)

>Given a two-dimensional array of integers, return the flattened version of the array with all the integers in the sorted (ascending) order.
>
>Example:
>
>Given [[3, 2, 1], [4, 6, 5], [], [9, 7, 8]], your function should return [1, 2, 3, 4, 5, 6, 7, 8, 9].
>
>Addendum:
>
>Please, keep in mind, that JavaScript is by default sorting objects alphabetically.

```javascript
// 1st try

```

## Get the mean of an array ( 8kyu )

: 평균값 구하기

> It's the academic year's end, fateful moment of your school report. The averages must be calculated. All the students come to you and entreat you to calculate their **average** for them. Easy ! You just need to write a script.
>
>Return the average of the given array **rounded down** to its nearest integer.
>
>The array will never be empty.

```javascript
//** MY solution **//
// 1st try
function getAverage(marks){
  let sum = 0; // 값을 0으로 초기화한 상태로 시작! 잊지 말 것
  //TODO : calculate the downward rounded average of the marks array
  for(let i = 0; i<marks.length; i++) {
    sum += Math.floor(marks[i]);
  }
  return sum / marks.length;
}
getAverage([2,2,2,2]); // 2
// -- FAILED -- expected 1.125 to equal 1


// 2nd try
function getAverage(marks){
  let sum = 0;
  //TODO : calculate the downward rounded average of the marks array
  for(let i = 0; i<marks.length; i++) {
    sum += marks[i];
  }
  return Math.floor(sum / marks.length);
}
getAverage([2,2,2,2]); // 2
// -- PASSED --
```

```javascript
//** BEST solution of oters **//
function getAverage(marks){
  return Math.floor(marks.reduce((sum, x) => sum + x) / marks.length);
}
// reduce!
```

## You only need one - Beginner ( 8kyu )

> You will be given an `array a` and a `value x`. All you need to do is check whether the provided `array` **contains** the `value`.
>
> Array can contain numbers or strings. X can be either.
>
> Return true if the array contains the value, false if not.

```javascript
//** MY solution **//
function check(a, x) {
  // your code here
  // array a가 요소 x를 포함하고 있는지 체크
  if (a.includes(x)) {
    return true;
  } else {
    return false;
  }
}

check([66,101], 66); // true
check(["what", "a", "great", "kata"], "kat"); // false
```

```javascript
//** BEST solution of others **//
const check = (a,x) => a.includes(x);
// 화살표함수! 익숙해지도록....!!
```

## Find the smallest integer in the array ( 8kyu ) (-ing)

> Given an array of integers your solution should find the **smallest integer**.
>
> For example:
>
> Given [34, 15, 88, 2] your solution will return 2
> Given [34, -345, -1, 100] your solution will return -345
> You can assume, for the purpose of this kata, that the supplied array will not be empty.

```javascript
class SmallestIntegerFinder {
  findSmallestInt(args) {
    
  }
}
```

## Count of positives / sum of negatives ( 8kyu ) (-ing)

> Given an array of integers.
>
> Return an array, where the first element is the count of positives numbers and the second element is sum of negative numbers.
>
> If the input array is empty or null, return an empty array.
>
> For example:
> For input [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, -11, -12, -13, -14, -15], you should return [10, -65].

```javascript
//** MY solution **//
// 1st try
function countPositivesSumNegatives(input) {
  let sum = 0;
  let result = []; // -- 빈 배열이 아닌 요소가 둘인 배열을 준비해도 ok. + input이 null이거나 empty일 때도 설정해야.
  for(let i = 0; i < input.length; i++) {
    if (input[i] > 0) {
      return input.length;
    } else {
      return sum += input[i];
    }
  }
    return resut.push(); // -- 1부터 잘못되었기 때문에 여기서 당연히 막힘.
}

// 2nd try
function countPositivesSumNegatives(input) {
  if(input == null || input === "") {
    return [];
  }
  
  let result = [];
  let countPos = 0;
  let sumNeg = 0;
  for(let i = 0; i < input.length; i++) {
    if (input[i] > 0) {
      countPos += 1;
    } else {
      sumNeg += input[i];
    }
    result.push(countPos);
    result.push(sumNeg);
  }
    return result;
}
```

## Counting sheep

>Consider an array/list of sheep where some sheep may be missing from their place. We need a function that **counts** the number of sheep present in the array (true means present).
>
> For example,
>
>[true,  true,  true,  false,
> true,  true,  true,  true ,
> true,  false, true,  false,
> true,  false, false, true ,
> true,  true,  true,  true ,
> false, false, true,  true]
> The correct answer would be 17.
>
> Hint: Don't forget to check for bad values like null/undefined

```javascript
//** MY solution **//
function countSheeps(array) {
  // TODO May the force be with you
  // Boolean을 사용해 fasle, 0, "", NaN, undefinded, null 등을 filter로 걸러낸 나머지를 배열의 요소로 반환
  return array.filter(Boolean).length;
}
```

```javascript
//** BEST solution of others **//
function countSheeps(arrayOfSheeps) {
  return arrayOfSheeps.filter(Boolean).length;
}
```

```javascript
//** ANOTHER solution **//
function countSheeps(arrayOfSheep) {
  // TODO May the force be with you
  var num = 0;
  
  for(var i = 0; i < arrayOfSheep.length; i++)
    if(arrayOfSheep[i] == true)
      num++;
      
  return num;
}
```

## Remove String Spaces ( 8kyu )

문자열 메소드

> Simple, **remove the spaces** from the string, then return the resultant string.

```javascript
function noSpace(x){
  // replace 정규표현식 사용 
  return x.replace(/ /gi,"");
}
```

## Even or odd ( 8kyu )

> Create a function that takes an `integer` as an argument and returns **"Even"** for even numbers or **"Odd"** for odd numbers.

```javascript
//** MY solution **//
function even_or_odd(number) {
  // 2로 나눴을 때 나머지가 0일 경우
  if (number % 2 === 0) {
    return "Even";
  } else {
    return "Odd";
  }  
}

even_or_odd(2); // Even
even_or_odd(7); // Odd
even_or_odd(-30); // Even
even_or_odd(-11); // Odd
even_or_odd(0); // Even
```

```javascript
//** BEST solution of others **//
function even_or_odd(number) {
  return number % 2 ? "Odd" : "Even"
}
// 삼항연산! 익숙해지기
```

## Abbreviate a Two Word Name

> Write a function to convert a name into initials. This kata strictly takes `two words with one space in between them`.
>
> The output should be **two capital letters** with a **dot** separating them.
>
> It should look like this:
>
> Sam Harris => S.H
> patrick feeney => P.F

- name을 two words로 각각 분리. - split()

- 각 문자열의 첫 글자를 찾고 capitalize. - map(), toUpperCase()

- "."을 기준을 결합 - join()

```javascript
//** MY solution **//
function abbrevName(name){
 return name
    // name을 two words로 split(글자 사이 space를 기준으로!)
   .split(" ")
    // split된 배열의 문자열 요소 각각의 첫번째 글자를 찾아 새로운 배열 생성 
   .map(str => str[0].toUpperCase()) // abbrevName("Sam Harris"); -> ["S", "H"] 
   .join("."); // "."을 기준으로 문자열로 변환
}
abbrevName("Sam Harris"); // 'S.H'
abbrevName("Tom Hody"); // 'P.F'
abbrevName("Robert Downy Junior"); // 'R.D.J'
```

```javascript
//** BEST solution of others **//
function abbrevName(name){

  var nameArray = name.split(" ");
  return (nameArray[0][0] + "." + nameArray[1][0]).toUpperCase();
  // array[0][0] 이런 식으로 써도 되는구나!
}
```

```javascript
//** ANOTHER solution **//
function abbrevName(name){
  return name.split(' ').map(x => x.substr(0, 1).toUpperCase()).join('.');
  // substr로 부분문자열 추출
}
```

### sources

Codewars

<https://www.codewars.com/>

# Kata in Codewars

## Sort and Star ~~(-ing)~~

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

## Replace With Alphabet Position

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

### sources

Training on Sort and Star | Codewars

<https://www.codewars.com/kata/57cfdf34902f6ba3d300001e/train/javascript>

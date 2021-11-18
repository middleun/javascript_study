# Kata in Codewars ( 7kyu )

## Flatten and sort an array ~~(-ing)~~

>Given a two-dimensional array of integers, return the `flattened version` of the array with all the integers in the **sorted** (ascending) order.
>
>Example:
>
>Given [[3, 2, 1], [4, 6, 5], [], [9, 7, 8]], your function should return [1, 2, 3, 4, 5, 6, 7, 8, 9].
>
>Addendum:
>
>Please, keep in mind, that JavaScript is by default sorting objects alphabetically.

: 배열 합치기 - concat / reduce를 사용해서 이전 값(배열)에 현재 값(배열)을 concat 후 sort로 정렬

- MY solution

```javascript
"use strict";

function flattenAndSort(array) {
  return array.reduce((prev, cur) => prev.concat(cur), []).sort((a, b) => a - b);
}

```

- BEST solution of others

```javascript
function flattenAndSort(array) {
  return [].concat(...array).sort((a,b) => a - b);
}
// spread operator 
```

- ANOTHER soltuion of others

```javascript
// 1
function flattenAndSort(array) {
  return array
    .reduce((result, current) => [...result, ...current],[])
    .sort((a, b) => a - b)
    ;
}
```

## Return the Missing Element

> Fellow code warrior, we need your help! We seem to have lost one of our sequence elements, and we need your help to retrieve it!
>
> Our sequence given was supposed to contain all of the integers from `0 to 9` (in no particular order), but `one` of them seems to be `missing`.
>
> Write a function that accepts a sequence of unique integers between 0 and 9 (inclusive), and returns the **missing element**.
>
> Examples:
> [0, 5, 1, 3, 2, 9, 7, 6, 4] --> 8
> [9, 2, 4, 5, 7, 0, 8, 6, 1] --> 3

- MY solution

```javascript
// 1st try
function getMissingElement(arr){
  return arr.filter((ele) => !0 <= ele || ele <=9)         
}
getMissingElement([0,5,1,3,2,9,7,6,4]); // (9) [0, 5, 1, 3, 2, 9, 7, 6, 4]
// !의 위치가?....

// 2nd try
function getMissingElement(arr){
  for(let i = 0; i < 10; i++) {
    if(!arr.includes(i)) {
      return i;
    }
  }
}
getMissingElement([0,5,1,3,2,9,7,6,4]); // 8
```

- BEST solution of others

```javascript
function getMissingElement(superImportantArray){
  for (i = 0; i < 10; i++) {
    if (superImportantArray.indexOf(i) === -1) return i;
  }
}
// 23indexOf!!
```

> [indexOf](../20_array_and_method_1.md#indexof)

- ANOTHER soltuions

```javascript
function getMissingElement(superImportantArray) {
  return superImportantArray.reduce(function (sum, value) {return sum - value;}, 45);
}
// 0 to 9으로 정해져있으니, 총합에서 나머지 요소의 누적값을 빼는 것도 방법! 와우.
```

## JavaScript Array Filter

> JavaScript Arrays support a filter function (starting in JavaScript 1.6). Use the filter functionality to complete the function given.
>
> The solution would work like the following:
>
> getEvenNumbers([2,4,5,6]) // should == [2,4,6]

- MY solution

```javascript
function getEvenNumbers(arr){
  // filter out the "odd" numbers
  // 짝수만 반환
  return arr.filter(ele => ele % 2 == 0);
}
```

## Convert an array of strings to array of numbers

> Some really funny web dev gave you a sequence of numbers from his API response as an sequence of strings!
>
> You need to cast the whole array to the correct type.
>
> Create the function that takes as a parameter a sequence of numbers represented as strings and outputs a sequence of numbers.
>
> ie:["1", "2", "3"] to [1, 2, 3]
>
> Note that you can receive floats as well.

- MY solution

```javascript
function toNumberArray(strArr){
  return strArr.map(ele => Number(ele));
}
toNumberArray(["1", "2", "3"]); // (3) [1, 2, 3]
toNumberArray(["1.1", "2.2", "3.3"]); // (3) [1.1, 2.2, 3.3]
```

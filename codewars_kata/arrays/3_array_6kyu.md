# Kata in Codewars ( 6kyu )

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

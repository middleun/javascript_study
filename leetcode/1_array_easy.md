# Problems in Leetcode ( easy )

## 53. Search Insert Position

> Given a sorted array of distinct integers and a target value, return the **index** if the `target` is found. If not, return the index **where it would be** if it were inserted in order.
>
> You must write an algorithm with O(log n) runtime complexity.

- MY solution

```javascript
// 1st try
var searchInsert = function(nums, target) {  
    return nums.indexOf(target);
};
searchInsert([1,3,5,6], 5); // 2
// test는 통과했으나 이 코드로는 target이 nums 안에 없을 때를 처리할 수 없음!
// target이 nums 안에 있을 때, 없을 때 나눠서. 

// 2nd try
var searchInsert = function(nums, target) {
    if(nums.includes(target)) {
        return nums.indexOf(target);    
    } else {
        nums.push(target);
        return nums.sort((a, b) => a - b).indexOf(target);
        // push하지 않은 상태. 원 배열을 그대로 둔 상태에서 하려면?...
    }
};
```

- OTHER solution

## 1. Two Sum

> Given an array of `integers nums` and an `integer target`, return indices of the two numbers such that they add up to target.
>
> You may assume that each input would have exactly one solution, and you may not use the same element twice.
>
> You can return the answer in any order.
>
> Example 1:
> Input: nums = [2,7,11,15], target = 9
> Output: [0,1]
> Output: Because nums[0] + nums[1] == 9, we return [0, 1].

- MY solution

```javascript
// 1st try
var twoSum = function(nums, target) {
    nums.reduce((i, j) => {
        if(nums[i] + nums[j] == target) {
            nums.push(i);
            nums.push(j);
            console.log(nums);
        }
        return nums;
        console.log(nums);
    }, []);
};

// 2nd try 
// 중첩 for문 사용
var twoSum = function(nums, target) {
    for(let i = 0; i < nums.length; i++) {
        for(let j = 1; j < nums.length; j++) {
            if(nums[i] + nums[j] == target && i != j) {
                return [i,j];
            }
        }
    }
};
```

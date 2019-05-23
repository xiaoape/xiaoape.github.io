---
layout: post
title: 删除数组中指定的元素
categories: Algorithm
description: 删除数组中指定的元素
keywords: 算法
---

一个数组里删除一个指定元素（数组里所有该元素都要删除），这里是在原数组上操作

``` javascript
var removeElement = function(nums, val) {
  for (var i = 0; i < nums.length; i++) {
    if (nums[i] == val) {
      nums.splice(i,1);
      i--;
    }
  }
  return nums.length;
};
```
在原数组中去掉元素不一定非要使用splice，还可以用重新赋值这样的方法，如num[i]=nums[i+1]来覆盖nums[i]。以leetcode中的移动零为例子：
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

示例:

输入: [0,1,0,3,12]
输出: [1,3,12,0,0]
说明:

必须在原数组上操作，不能拷贝额外的数组。
尽量减少操作次数。

```javascript
//使用splice的方法
var moveZeroes = function(nums) {
    let r = nums.length;
    for(let i =0;i<nums.length;i++){
        if(nums[i]==0){
            nums.splice(i,1);
            i--;
        }
    }
    let p =r-nums.length
    for(let j=0;j<p;j++){
        nums.push(0)
    }
}

//使用原数组元素覆盖原数组元素的方法
var moveZeroes = function(nums) {
  let length = nums.length
  //nums = nums.filter( i=> i !== 0)  // no use filter, it news a new array
  let j = 0
  for (let i = 0; i < length; i++) {
    if (nums[i] !== 0) {
      nums[j] = nums[i]
      j++
    }
  }
  let index = j 
  length = length - index
  for (let i = 0; i < length; i++) {
    nums[index + i] = 0
  }
};
```

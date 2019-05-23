---
layout: post
title: 数组里只出现一次的数字
categories: Algorithm
description: 数组里只出现一次的数字
keywords: 算法
---

题目描述:给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

示例 1:

输入: [2,2,1]
输出: 1
示例 2:

输入: [4,1,2,1,2]
输出: 4 
``` javascript
//第一次出现将该属性值设为true，第二次出现就删了它，最后就只剩下一个唯一出现的数字
var singleNumber = function(nums) {
  var cache = {};
  
  nums.forEach(function (num) {
    if (cache[num])
      delete cache[num];
    else
      cache[num] = true;
  });
  
  return parseInt(Object.keys(cache)[0], 10);
};
//类似的方法
var findDuplicates = function(nums) {
    var arr = []
    var chase = {}
    for(let i = 0;i<nums.length;i++){
        if(chase[nums[i]]){
            arr.push(chase[nums[i]])
        }else
            chase[nums[i]]= nums[i]
    }
    return arr
};
```
给定一个大小为 n 的数组，找到其中的众数。众数是指在数组中出现次数大于 ⌊ n/2 ⌋ 的元素。

你可以假设数组是非空的，并且给定的数组总是存在众数。

示例 1:

输入: [3,2,3]
输出: 3
示例 2:

输入: [2,2,1,1,1,2,2]
输出: 2
``` javascript
var majorityElement = function(nums) {
    var len = nums.length;
    var halfLen = len / 2;
    var item;
    var cache = {};
    for (var i = 0; i < len; i++) {
        item = nums[i];
        if (cache[item] === undefined) {
            cache[item] = 1;
        } else {
            cache[item]++;
        }
        if (cache[item] > halfLen) {
            return item;
        }
    }
};
```
---
id: two-sum
title: Two Sum
sidebar_label: Two Sum
---
## Description
<div class="description">
<p>Given an array of integers, return <strong>indices</strong> of the two numbers such that they add up to a specific target.</p>

<p>You may assume that each input would have <strong><em>exactly</em></strong> one solution, and you may not use the <em>same</em> element twice.</p>

<p><strong>Example:</strong></p>

<pre>
Given nums = [2, 7, 11, 15], target = 9,

Because nums[<strong>0</strong>] + nums[<strong>1</strong>] = 2 + 7 = 9,
return [<strong>0</strong>, <strong>1</strong>].
</pre>

<p>&nbsp;</p>

</div>

## Solution
```javascript
var twoSum = function(nums, target) {

    for(var i = 0; i < nums.length; i++) {
        for(var j = i + 1; j< nums.length; j++){
            if(nums[i] + nums[j] == target){
                return [i,j];
            }
        }
    }
};

```
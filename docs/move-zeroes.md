---
id: move-zeroes
title: Move Zeroes
sidebar_label: Move Zeroes
---
## Description
<div class="description">
<p>Given an array <code>nums</code>, write a function to move all <code>0</code>&#39;s to the end of it while maintaining the relative order of the non-zero elements.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b> <code>[0,1,0,3,12]</code>
<b>Output:</b> <code>[1,3,12,0,0]</code></pre>

<p><b>Note</b>:</p>

<ol>
	<li>You must do this <b>in-place</b> without making a copy of the array.</li>
	<li>Minimize the total number of operations.</li>
</ol>
</div>

## Solution(javascript)
```javascript
/**
 * @param {number[]} nums
 * @return {void} Do not return anything, modify nums in-place instead.
 */
var moveZeroes = function(nums) {
    let counter = 0,
        index = nums.indexOf(0);
        while(index !== -1){
            counter++;
            nums.splice(index, 1);
            index = nums.indexOf(0);
        }

    for(let i = 0; i < counter; i++){
        nums.push(0);
    }    
    
};
```
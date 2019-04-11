---
id: intersection-of-two-arrays
title: Intersection of Two Arrays
sidebar_label: Intersection of Two Arrays
---
## Description
<div class="description">
<p>Given two arrays, write a function to compute their intersection.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>nums1 = <span id="example-input-1-1">[1,2,2,1]</span>, nums2 = <span id="example-input-1-2">[2,2]</span>
<strong>Output: </strong><span id="example-output-1">[2]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>nums1 = <span id="example-input-2-1">[4,9,5]</span>, nums2 = <span id="example-input-2-2">[9,4,9,8,4]</span>
<strong>Output: </strong><span id="example-output-2">[9,4]</span></pre>
</div>

<p><b>Note:</b></p>

<ul>
	<li>Each element in the result must be unique.</li>
	<li>The result can be in any order.</li>
</ul>

<p>&nbsp;</p>

</div>

## Solution
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number[]}
 */
var intersection = function(nums1, nums2) {
    let newArr = [];
    for(let i = 0; i < nums1.length; i++){
        if(nums2.indexOf(nums1[i]) !== -1){
            newArr.push(nums1[i]);
        }
    }
    
    let set = new Set(newArr);
    return [...set];
};
```
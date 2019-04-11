---
id: binary-search
title: Binary Search
sidebar_label: Binary Search
---
## Description
<div class="description">
<p>Given a <strong>sorted</strong> (in ascending order) integer array <code>nums</code> of <code>n</code> elements and a <code>target</code> value, write a function to search <code>target</code> in <code>nums</code>. If <code>target</code> exists, then return its index, otherwise return <code>-1</code>.</p>

<p><br />
<strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <code>nums</code> = [-1,0,3,5,9,12], <code>target</code> = 9
<strong>Output:</strong> 4
<strong>Explanation:</strong> 9 exists in <code>nums</code> and its index is 4

</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <code>nums</code> = [-1,0,3,5,9,12], <code>target</code> = 2
<strong>Output:</strong> -1
<strong>Explanation:</strong> 2 does not exist in <code>nums</code> so return -1
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ol>
	<li>You may assume that all elements in <code>nums</code> are unique.</li>
	<li><code>n</code> will be in the range <code>[1, 10000]</code>.</li>
	<li>The value of each element in <code>nums</code> will be in the range <code>[-9999, 9999]</code>.</li>
</ol>

</div>

## Solution
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
const search = (nums, target) => {
  const aux = (low, high) => {
    if (low > high) {
      return -1
    }
    const middle = Math.floor((low + high) / 2)
    if (nums[middle] === target) {
      return middle
    } if (nums[middle] < target) {
      return aux(middle + 1, high)
    }
    return aux(low, middle - 1)
  }
  return aux(0, nums.length - 1)
}

```
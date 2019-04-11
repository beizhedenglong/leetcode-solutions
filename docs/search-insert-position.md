---
id: search-insert-position
title: Search Insert Position
sidebar_label: Search Insert Position
---
## Description
<div class="description">
<p>Given a sorted array and a target value, return the index if the target is found. If not, return the index where it would be if it were inserted in order.</p>

<p>You may assume no duplicates in the array.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 5
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 2
<strong>Output:</strong> 1
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 7
<strong>Output:</strong> 4
</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> [1,3,5,6], 0
<strong>Output:</strong> 0
</pre>

</div>

## Solution
```javascript
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number}
 */
const searchInsert = (nums, target) => {
  const aux = (low, high) => {
    if (low > high) {
      return low
    }
    const middle = Math.floor((low + high) / 2)
    if (target === nums[middle]) {
      return middle
    } if (target > nums[middle]) {
      return aux(middle + 1, high)
    }
    return aux(low, middle - 1)
  }
  return aux(0, nums.length - 1)
}

```
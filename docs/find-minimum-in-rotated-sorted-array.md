---
id: find-minimum-in-rotated-sorted-array
title: Find Minimum in Rotated Sorted Array
sidebar_label: Find Minimum in Rotated Sorted Array
---
## Description
<div class="description">
<p>Suppose an array sorted in ascending order is rotated at some pivot unknown to you beforehand.</p>

<p>(i.e., &nbsp;<code>[0,1,2,4,5,6,7]</code>&nbsp;might become &nbsp;<code>[4,5,6,7,0,1,2]</code>).</p>

<p>Find the minimum element.</p>

<p>You may assume no duplicate exists in the array.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> [3,4,5,1,2] 
<strong>Output:</strong> 1
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> [4,5,6,7,0,1,2]
<strong>Output:</strong> 0
</pre>

</div>

## Solution(javascript)
```javascript
/*
 * @lc app=leetcode id=153 lang=javascript
 *
 * [153] Find Minimum in Rotated Sorted Array
 *
 * https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/description/
 *
 * algorithms
 * Medium (42.57%)
 * Total Accepted:    264.9K
 * Total Submissions: 622.2K
 * Testcase Example:  '[3,4,5,1,2]'
 *
 * Suppose an array sorted in ascending order is rotated at some pivot unknown
 * to you beforehand.
 *
 * (i.e.,  [0,1,2,4,5,6,7] might become  [4,5,6,7,0,1,2]).
 *
 * Find the minimum element.
 *
 * You may assume no duplicate exists in the array.
 *
 * Example 1:
 *
 *
 * Input: [3,4,5,1,2]
 * Output: 1
 *
 *
 * Example 2:
 *
 *
 * Input: [4,5,6,7,0,1,2]
 * Output: 0
 *
 *
 */
/**
 * @param {number[]} nums
 * @return {number}
 */
const findMin = (nums) => {
  let low = 0
  let high = nums.length - 1
  if (nums[high] >= nums[low]) {
    return nums[low]
  }
  while (low <= high) {
    const middle = Math.floor((low + high) / 2)
    // console.log(nums[low], nums[middle], nums[high])
    if (nums[middle] < nums[middle - 1]) {
      return nums[middle]
    }
    if (nums[middle + 1] < nums[middle]) {
      return nums[middle + 1]
    }
    if (nums[middle] > nums[0]) {
      low = middle + 1
    } else if (nums[middle] < nums[nums.length - 1]) {
      high = middle - 1
    }
  }
}
// console.log(findMin([4, 5, 6, 7, 0, 1, 2]))

```
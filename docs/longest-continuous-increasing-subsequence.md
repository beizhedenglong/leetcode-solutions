---
id: longest-continuous-increasing-subsequence
title: Longest Continuous Increasing Subsequence
sidebar_label: Longest Continuous Increasing Subsequence
---
## Description
<div class="description">
<p>
Given an unsorted array of integers, find the length of longest <code>continuous</code> increasing subsequence (subarray).
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [1,3,5,4,7]
<b>Output:</b> 3
<b>Explanation:</b> The longest continuous increasing subsequence is [1,3,5], its length is 3. 
Even though [1,3,5,7] is also an increasing subsequence, it's not a continuous one where 5 and 7 are separated by 4. 
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> [2,2,2,2,2]
<b>Output:</b> 1
<b>Explanation:</b> The longest continuous increasing subsequence is [2], its length is 1. 
</pre>
</p>

<p><b>Note:</b>
Length of the array will not exceed 10,000.
</p>
</div>

## Solution
```javascript
/**
 * @param {number[]} nums
 * @return {number}
 */
const findLengthOfLCIS = function (nums) {
  let maxLength = 0
  let currentLength = 0
  for (let i = 0; i < nums.length; i++) {
    if ((i === 0) || (nums[i] > nums[i - 1])) {
      currentLength += 1
    } else {
      currentLength = 1
    }
    maxLength = currentLength > maxLength ? currentLength : maxLength
  }
  return maxLength
}
```
---
id: merge-sorted-array
title: Merge Sorted Array
sidebar_label: Merge Sorted Array
---
## Description
<div class="description">
<p>Given two sorted integer arrays <em>nums1</em> and <em>nums2</em>, merge <em>nums2</em> into <em>nums1</em> as one sorted array.</p>

<p><strong>Note:</strong></p>

<ul>
	<li>The number of elements initialized in <em>nums1</em> and <em>nums2</em> are <em>m</em> and <em>n</em> respectively.</li>
	<li>You may assume that <em>nums1</em> has enough space (size that is greater or equal to <em>m</em> + <em>n</em>) to hold additional elements from <em>nums2</em>.</li>
</ul>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>
nums1 = [1,2,3,0,0,0], m = 3
nums2 = [2,5,6],       n = 3

<strong>Output:</strong>&nbsp;[1,2,2,3,5,6]
</pre>

</div>

## Solution
```javascript
/**
 * @param {number[]} nums1
 * @param {number} m
 * @param {number[]} nums2
 * @param {number} n
 * @return {void} Do not return anything, modify nums1 in-place instead.
 */
const merge = (nums1, m, nums2, n) => {
  const aux = (arr1 = [], arr2 = [], bound, counter1, counter2) => {
    if (counter2 >= nums2.length) {
      return
    }
    if ((arr1[counter1] <= arr2[counter2]) && (counter1 <= bound)) {
      return aux(arr1, arr2, bound, counter1 + 1, counter2)
    }
    if (counter1 <= bound) {
      arr1.splice(counter1, 0, arr2[counter2])
      arr1.splice(arr1.length - 1, 1)
      return aux(arr1, arr2, bound + 1, counter1, counter2 + 1)
    }
    arr1.splice(counter1, 1, arr2[counter2])
    return aux(arr1, arr2, bound, counter1 + 1, counter2 + 1)
  }
  aux(nums1, nums2, m - 1, 0, 0)
}
```
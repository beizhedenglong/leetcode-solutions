---
id: median-of-two-sorted-arrays
title: Median of Two Sorted Arrays
sidebar_label: Median of Two Sorted Arrays
---
## Description
<div class="description">
<p>There are two sorted arrays <b>nums1</b> and <b>nums2</b> of size m and n respectively.</p>

<p>Find the median of the two sorted arrays. The overall run time complexity should be O(log (m+n)).</p>

<p>You may assume <strong>nums1</strong> and <strong>nums2</strong>&nbsp;cannot be both empty.</p>

<p><b>Example 1:</b></p>

<pre>
nums1 = [1, 3]
nums2 = [2]

The median is 2.0
</pre>

<p><b>Example 2:</b></p>

<pre>
nums1 = [1, 2]
nums2 = [3, 4]

The median is (2 + 3)/2 = 2.5
</pre>

</div>

## Solution
```javascript
/**
 * @param {number[]} nums1
 * @param {number[]} nums2
 * @return {number}
 */
const findMedianSortedArrays = (nums1, nums2) => {
  const merge = (xs1, xs2) => {
    if (!xs1 || !xs1.length) {
      return xs2
    }
    if (!xs2 || !xs2.length) {
      return xs1
    }
    const [hd1, ...rest1] = xs1
    const [hd2, ...rest2] = xs2
    return hd1 <= hd2 ? [hd1, ...merge(rest1, xs2)] : [hd2, ...merge(xs1, rest2)]
  }
  const nums = merge(nums1, nums2)
  const middle = Math.floor((nums.length-1) / 2)

  return (middle * 2 === (nums.length-1)) ?  nums[middle] : ((nums[middle] + nums[middle + 1]) / 2) 
}

```
---
id: convert-sorted-array-to-binary-search-tree
title: Convert Sorted Array to Binary Search Tree
sidebar_label: Convert Sorted Array to Binary Search Tree
---
## Description
<div class="description">
<p>Given an array where elements are sorted in ascending order, convert it to a height balanced BST.</p>

<p>For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of <em>every</em> node never differ by more than 1.</p>

<p><strong>Example:</strong></p>

<pre>
Given the sorted array: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
</pre>

</div>

## Solution(javascript)
```javascript

/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {number[]} nums
 * @return {TreeNode}
 */
const sortedArrayToBST = (nums = []) => {
  const aux = (low, high) => {
    if (low <= high) {
      const middle = Math.floor((low + high) / 2)
      const node = {
        val: nums[middle],
      }
      node.left = aux(low, middle - 1)
      node.right = aux(middle + 1, high)
      return node
    }
    return null
  }
  return aux(0, nums.length - 1)
}

```
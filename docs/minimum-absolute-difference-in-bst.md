---
id: minimum-absolute-difference-in-bst
title: Minimum Absolute Difference in BST
sidebar_label: Minimum Absolute Difference in BST
---
## Description
<div class="description">
<p>Given a binary search tree with non-negative values, find the minimum <a href="https://en.wikipedia.org/wiki/Absolute_difference">absolute difference</a> between values of any two nodes.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b>

   1
    \
     3
    /
   2

<b>Output:</b>
1

<b>Explanation:</b>
The minimum absolute difference is 1, which is the difference between 2 and 1 (or between 2 and 3).
</pre>

<p>&nbsp;</p>

<p><b>Note:</b> There are at least two nodes in this BST.</p>

</div>

## Solution
```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
const getMinimumDifference = (root) => {
  let min = Infinity
  let previous = null
  const aux = (node) => {
    if (!node) {
      return
    }
    if (node.left) {
      aux(node.left)
    }
    const possibleMin = Math.abs(node.val - previous)
    if ((previous !== null) && (possibleMin < min)) {
      min = possibleMin
    }
    previous = node.val
    if (node.right) {
      aux(node.right)
    }
  }
  aux(root)
  return min
}

```
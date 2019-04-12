---
id: sum-of-left-leaves
title: Sum of Left Leaves
sidebar_label: Sum of Left Leaves
---
## Description
<div class="description">
<p>Find the sum of all left leaves in a given binary tree.</p>

<p><b>Example:</b>
<pre>
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values <b>9</b> and <b>15</b> respectively. Return <b>24</b>.
</pre>
</p>
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
 * @param {TreeNode} root
 * @return {number}
 */
const sumOfLeftLeaves = (root) => {
  let sum = 0
  const aux = (node) => {
    if (!node) {
      return
    }
    if (node.left) {
      aux(node.left)
    }
    if (node.left && !node.left.left && !node.left.right) {
      sum += node.left.val
    }
    if (node.right) {
      aux(node.right)
    }
  }
  aux(root)
  return sum
}

```
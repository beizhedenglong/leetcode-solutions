---
id: trim-a-binary-search-tree
title: Trim a Binary Search Tree
sidebar_label: Trim a Binary Search Tree
---
## Description
<div class="description">
<p>
Given a binary search tree and the lowest and highest boundaries as <code>L</code> and <code>R</code>, trim the tree so that all its elements lies in <code>[L, R]</code> (R >= L). You might need to change the root of the tree, so the result should return the new root of the trimmed binary search tree.
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> 
    1
   / \
  0   2

  L = 1
  R = 2

<b>Output:</b> 
    1
      \
       2
</pre>
</p>

<p><b>Example 2:</b><br />
<pre>
<b>Input:</b> 
    3
   / \
  0   4
   \
    2
   /
  1

  L = 1
  R = 3

<b>Output:</b> 
      3
     / 
   2   
  /
 1
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
 * @param {number} L
 * @param {number} R
 * @return {TreeNode}
 */
const trimBST = function (root, L, R) {
  if (root) {
    if (root.val < L) {
      return trimBST(root.right, L, R)
    }
    if (root.val > R) {
      return trimBST(root.left, L, R)
    }
    root.left = trimBST(root.left, L, R)
    root.right = trimBST(root.right, L, R)
  }
  return root
}
```
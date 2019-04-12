---
id: balanced-binary-tree
title: Balanced Binary Tree
sidebar_label: Balanced Binary Tree
---
## Description
<div class="description">
<p>Given a binary tree, determine if it is height-balanced.</p>

<p>For this problem, a height-balanced binary tree is defined as:</p>

<blockquote>
<p>a binary tree in which the depth of the two subtrees of <em>every</em> node never differ by more than 1.</p>
</blockquote>

<p><strong>Example 1:</strong></p>

<p>Given the following tree <code>[3,9,20,null,null,15,7]</code>:</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7</pre>

<p>Return true.<br />
<br />
<strong>Example 2:</strong></p>

<p>Given the following tree <code>[1,2,2,3,3,null,null,4,4]</code>:</p>

<pre>
       1
      / \
     2   2
    / \
   3   3
  / \
 4   4
</pre>

<p>Return false.</p>

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
 * @return {boolean}
 */
const isBalanced = (root) => {
  const height = (node, currentHeight) => {
    if (!node) {
      return currentHeight
    }
    let leftHeight = currentHeight
    let rightHeight = currentHeight
    if (node.left) {
      leftHeight = height(node.left, currentHeight + 1)
    }
    if (node.right) {
      rightHeight = height(node.right, currentHeight + 1)
    }
    return leftHeight > rightHeight ? leftHeight : rightHeight
  }
  if (!root) {
    return true
  }
  const leftHeight = root.left ? height(root.left, 1) : 0
  const rightHeight = root.right ? height(root.right, 1) : 0
  if (
    (Math.abs(leftHeight - rightHeight) <= 1) && isBalanced(root.left) && isBalanced(root.right)
  ) {
    return true
  }
  return false
}

```
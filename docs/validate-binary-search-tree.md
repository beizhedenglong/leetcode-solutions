---
id: validate-binary-search-tree
title: Validate Binary Search Tree
sidebar_label: Validate Binary Search Tree
---
## Description
<div class="description">
<p>Given a binary tree, determine if it is a valid binary search tree (BST).</p>

<p>Assume a BST is defined as follows:</p>

<ul>
	<li>The left subtree of a node contains only nodes with keys <strong>less than</strong> the node&#39;s key.</li>
	<li>The right subtree of a node contains only nodes with keys <strong>greater than</strong> the node&#39;s key.</li>
	<li>Both the left and right subtrees must also be binary search trees.</li>
</ul>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong>
    2
   / \
  1   3
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
    5
   / \
  1   4
&nbsp;    / \
&nbsp;   3   6
<strong>Output:</strong> false
<strong>Explanation:</strong> The input is: [5,1,4,null,null,3,6]. The root node&#39;s value
&nbsp;            is 5 but its right child&#39;s value is 4.
</pre>

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
 * @return {boolean}
 */
const isValidBST = (root) => {
  let prev = null
  const aux = (node) => {
    if (node) {
      const isLeftValid = aux(node.left)
      let currentValid = true
      if (prev !== null && prev >= node.val) {
        currentValid = false
      }
        prev = node.val
      const isRightValid = aux(node.right)
      return isLeftValid && isRightValid && currentValid
    }
    return true
  }
  return aux(root)
}

```
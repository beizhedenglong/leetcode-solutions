---
id: construct-binary-tree-from-preorder-and-inorder-traversal
title: Construct Binary Tree from Preorder and Inorder Traversal
sidebar_label: Construct Binary Tree from Preorder and Inorder Traversal
---
## Description
<div class="description">
<p>Given preorder and inorder traversal of a tree, construct the binary tree.</p>

<p><strong>Note:</strong><br />
You may assume that duplicates do not exist in the tree.</p>

<p>For example, given</p>

<pre>
preorder =&nbsp;[3,9,20,15,7]
inorder = [9,3,15,20,7]</pre>

<p>Return the following binary tree:</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7</pre>

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
 * @param {number[]} preorder
 * @param {number[]} inorder
 * @return {TreeNode}
 */
const buildTree = (preorder, inorder) => {
  if (preorder.length === 0) {
    return null
  }

  const node = {
    val: preorder[0],
    left: null,
    right: null,
  }
  const index = inorder.findIndex(v => v === preorder[0])
  node.left = buildTree(preorder.slice(1, 1 + index), inorder.slice(0, index))
  node.right = buildTree(preorder.slice(1 + index), inorder.slice(index + 1))
  return node
}
```
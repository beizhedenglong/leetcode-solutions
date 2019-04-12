---
id: flatten-binary-tree-to-linked-list
title: Flatten Binary Tree to Linked List
sidebar_label: Flatten Binary Tree to Linked List
---
## Description
<div class="description">
<p>Given a binary tree, flatten it to a linked list in-place.</p>

<p>For example, given the following tree:</p>

<pre>
    1
   / \
  2   5
 / \   \
3   4   6
</pre>

<p>The flattened tree should look like:</p>

<pre>
1
 \
  2
   \
    3
     \
      4
       \
        5
         \
          6
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
 * @param {TreeNode} root
 * @return {void} Do not return anything, modify root in-place instead.
 */
const flatten = function (root) {
  const inorderTraverse = (node, res = []) => {
    if (node) {
      res.push(node)
      inorderTraverse(node.left, res)
      inorderTraverse(node.right, res)
    }
    return res
  }
  const nodes = inorderTraverse(root)
  nodes.forEach((node, index) => {
    node.left = null
    if (nodes[index + 1]) {
      node.right = nodes[index + 1]
    } else {
      node.right = null
    }
  })
}
```
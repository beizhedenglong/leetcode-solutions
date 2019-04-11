---
id: binary-tree-level-order-traversal
title: Binary Tree Level Order Traversal
sidebar_label: Binary Tree Level Order Traversal
---
## Description
<div class="description">
<p>Given a binary tree, return the <i>level order</i> traversal of its nodes' values. (ie, from left to right, level by level).</p>

<p>
For example:<br />
Given binary tree <code>[3,9,20,null,null,15,7]</code>,<br />
<pre>
    3
   / \
  9  20
    /  \
   15   7
</pre>
</p>
<p>
return its level order traversal as:<br />
<pre>
[
  [3],
  [9,20],
  [15,7]
]
</pre>
</p>
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
 * @return {number[][]}
 */
const levelOrder = (root) => {
  const aux = (node, level, acc) => {
    if (!node) {
      return acc
    }
    if (node.left) {
      aux(node.left, level + 1, acc)
    }
    if (acc[level]) {
      acc[level].push(node.val)
    } else {
      acc[level] = [node.val]
    }
    if (node.right) {
      aux(node.right, level + 1, acc)
    }
    return acc
  }
  return aux(root, 0, [])
}

```
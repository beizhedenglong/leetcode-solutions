---
id: binary-tree-level-order-traversal-ii
title: Binary Tree Level Order Traversal II
sidebar_label: Binary Tree Level Order Traversal II
---
## Description
<div class="description">
<p>Given a binary tree, return the <i>bottom-up level order</i> traversal of its nodes' values. (ie, from left to right, level by level from leaf to root).</p>

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
return its bottom-up level order traversal as:<br />
<pre>
[
  [15,7],
  [9,20],
  [3]
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
const levelOrderBottom = (root) => {
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
  return aux(root, 0, []).reverse()
}

```
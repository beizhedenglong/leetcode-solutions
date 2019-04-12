---
id: minimum-depth-of-binary-tree
title: Minimum Depth of Binary Tree
sidebar_label: Minimum Depth of Binary Tree
---
## Description
<div class="description">
<p>Given a binary tree, find its minimum depth.</p>

<p>The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<p>Given binary tree <code>[3,9,20,null,null,15,7]</code>,</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7</pre>

<p>return its minimum&nbsp;depth = 2.</p>

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
const minDepth = (root) => {
  if (!root) {
    return 0
  }
  const aux = (node, depth) => {
    if (!node || (!node.left && !node.right)) {
      return depth
    }

    if (node.left && !node.right) {
      return aux(node.left, depth + 1)
    }
    if (node.right && !node.left) {
      return aux(node.right, depth + 1)
    }
    const leftDepth = aux(node.left, depth + 1)
    const rightDepth = aux(node.right, depth + 1)
    return leftDepth < rightDepth ? leftDepth : rightDepth
  }
  return aux(root, 1)
}

```
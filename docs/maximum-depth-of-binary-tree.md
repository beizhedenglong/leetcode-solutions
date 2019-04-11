---
id: maximum-depth-of-binary-tree
title: Maximum Depth of Binary Tree
sidebar_label: Maximum Depth of Binary Tree
---
## Description
<div class="description">
<p>Given a binary tree, find its maximum depth.</p>

<p>The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<p>Given binary tree <code>[3,9,20,null,null,15,7]</code>,</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7</pre>

<p>return its depth = 3.</p>

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
const maxDepth = (root) => {
  if (!root) {
    return 0
  }
  const stack = []
  let max = 0
  const getHeight = () => (stack.length ? stack[stack.length - 1].height : 0)
  const push = (node, height) => {
    while (node) {
      height = height != null ? height + 1 : getHeight() + 1
      stack.push({ node, height })
      if (height > max) {
        max = height
      }
      node = node.left
    }
  }
  const pop = () => {
    while (stack.length) {
      const last = stack.pop()
      if (last.node.right) {
        push(last.node.right, last.height)
      }
    }
  }
  push(root)
  pop()
  return max
}

```
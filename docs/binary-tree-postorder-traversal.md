---
id: binary-tree-postorder-traversal
title: Binary Tree Postorder Traversal
sidebar_label: Binary Tree Postorder Traversal
---
## Description
<div class="description">
<p>Given a binary tree, return the <em>postorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;<code>[1,null,2,3]</code>
   1
    \
     2
    /
   3

<strong>Output:</strong>&nbsp;<code>[3,2,1]</code>
</pre>

<p><strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?</p>

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
 * @return {number[]}
 */
// const postorderTraversal = (root) => {
//   const aux = (node, acc) => {
//     if (node) {
//       aux(node.left, acc)
//       aux(node.right, acc)
//       acc.push(node.val)
//     }
//     return acc
//   }
//   return aux(root, [])
// }

const postorderTraversal = (root) => {
  const stack = []
  const res = []
  const push = (node) => {
    if (node) {
      stack.push(node)
    }
  }
  const pop = () => {
    while (stack.length) {
      const node = stack.pop()
      res.unshift(node.val)

      push(node.left)
      push(node.right)
    }
  }
  push(root)
  pop()
  return res
}

```
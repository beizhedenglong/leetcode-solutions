---
id: binary-tree-preorder-traversal
title: Binary Tree Preorder Traversal
sidebar_label: Binary Tree Preorder Traversal
---
## Description
<div class="description">
<p>Given a binary tree, return the <em>preorder</em> traversal of its nodes&#39; values.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;<code>[1,null,2,3]</code>
   1
    \
     2
    /
   3

<strong>Output:</strong>&nbsp;<code>[1,2,3]</code>
</pre>

<p><strong>Follow up:</strong> Recursive solution is trivial, could you do it iteratively?</p>

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
 * @return {number[]}
 */
// const preorderTraversal = (root) => {
//   const aux = (node, acc = []) => {
//     if (node) {
//       acc.push(node.val)
//       aux(node.left, acc)
//       aux(node.right, acc)
//     }
//     return acc
//   }
//   return aux(root)
// }

const preorderTraversal = (root) => {
  const stack = []
  const res = []
  const push = (node) => {
    let current = node
    while (current) {
      res.push(current.val)
      if (current.right) {
        stack.push(current.right)
      }
      current = current.left
    }
  }
  const pop = () => {
    while (stack.length) {
      push(stack.pop())
    }
  }
  push(root)
  pop()
  return res
}

```
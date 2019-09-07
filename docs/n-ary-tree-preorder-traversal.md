---
id: n-ary-tree-preorder-traversal
title: N-ary Tree Preorder Traversal
sidebar_label: N-ary Tree Preorder Traversal
---
## Description
<div class="description">
<p>Given an n-ary tree, return the <i>preorder</i> traversal of its nodes&#39; values.</p>

<p>For example, given a <code>3-ary</code> tree:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;" /></p>

<p>&nbsp;</p>

<p>Return its preorder traversal as: <code>[1,3,5,6,2,4]</code>.</p>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<p>Recursive solution is trivial, could you do it iteratively?</p>

</div>

## Solution(javascript)
```javascript
// Recursive
// const preorder = function (root) {
//   let acc = []
//   const aux = (node) => {
//     console.log(acc)
//     if (!node) {
//       return acc
//     }
//     acc.push(node.val)
//     if (node.children) {
//       node.children.forEach((child) => {
//         acc = aux(child)
//       })
//     }
//     return acc
//   }
//   return aux(root)
// }

// Iterative

const preorder = (root) => {
  const result = []
  const stack = []
  if (root) {
    stack.push(root)
  }
  while (stack.length > 0) {
    const node = stack.pop()
    result.push(node.val)
    if (node.children) {
      for (let i = node.children.length - 1; i >= 0; i--) {
        stack.push(node.children[i])
      }
    }
  }
  return result
}


preorder({
  val: 1,
  children: [{
    val: 2,
  }],
})

```
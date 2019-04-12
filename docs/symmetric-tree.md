---
id: symmetric-tree
title: Symmetric Tree
sidebar_label: Symmetric Tree
---
## Description
<div class="description">
<p>Given a binary tree, check whether it is a mirror of itself (ie, symmetric around its center).</p>

<p>
For example, this binary tree <code>[1,2,2,3,4,4,3]</code> is symmetric:
<pre>
    1
   / \
  2   2
 / \ / \
3  4 4  3
</pre>
</p>
<p>
But the following <code>[1,2,2,null,3,null,3]</code>  is not:<br />
<pre>
    1
   / \
  2   2
   \   \
   3    3
</pre>
</p>

<p>
<b>Note:</b><br />
Bonus points if you could solve it both recursively and iteratively.
</p>
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
 * @return {boolean}
 */
// const isSymmetric = function (root) {
//   if (!root) {
//     return true
//   }
//   const isSymmetricHelper = (arr = []) => {
//     const values = arr.map(node => (node ? node.val : null))
//     for (let i = 0; i <= values.length / 2; i++) {
//       if (values[i] !== values[values.length - 1 - i]) {
//         return false
//       }
//     }
//     return true
//   }
//   let frontier = [root]
//   while (frontier.length) {
//     const next = []
//     frontier.forEach((node) => {
//       if (node) {
//         next.push(node.left)
//         next.push(node.right)
//       }
//     })
//     if (!isSymmetricHelper(frontier)) {
//       return false
//     }
//     frontier = next
//   }
//   return true
// }

// recursive version
const isSymmetric = function (root) {
  const aux = (node, level, result) => {
    if (!result[level]) {
      result[level] = []
    }
    if (!node) {
      result[level].push(null)
      return result
    }
    result[level].push(node.val)
    aux(node.left, level + 1, result)
    aux(node.right, level + 1, result)
    return result
  }
  const isSymmetricHelper = (values = []) => {
    for (let i = 0; i <= values.length / 2; i++) {
      if (values[i] !== values[values.length - 1 - i]) {
        return false
      }
    }
    return true
  }
  const result = aux(root, 0, [])
  for (let i = 0; i < result.length; i++) {
    if (!isSymmetricHelper(result[i])) {
      return false
    }
  }
  return true
}

```
---
id: find-largest-value-in-each-tree-row
title: Find Largest Value in Each Tree Row
sidebar_label: Find Largest Value in Each Tree Row
---
## Description
<div class="description">
<p>You need to find the largest value in each row of a binary tree.</p>

<p><b>Example:</b><br />
<pre>
<b>Input:</b> 

          1
         / \
        3   2
       / \   \  
      5   3   9 

<b>Output:</b> [1, 3, 9]
</pre>
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
 * @return {number[]}
 */
const largestValues = (root) => {
  const res = []
  if (!root) {
    return res
  }
  let frontier = [root]
  while (frontier.length) {
    const next = []
    let max = -Infinity
    frontier.forEach((node) => {
      if (node.val > max) {
        max = node.val
      }
      if (node.left) {
        next.push(node.left)
      }
      if (node.right) {
        next.push(node.right)
      }
    })
    frontier = next
     res.push(max)
  }
  return res
}

```
---
id: average-of-levels-in-binary-tree
title: Average of Levels in Binary Tree
sidebar_label: Average of Levels in Binary Tree
---
## Description
<div class="description">
Given a non-empty binary tree, return the average value of the nodes on each level in the form of an array.

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b>
    3
   / \
  9  20
    /  \
   15   7
<b>Output:</b> [3, 14.5, 11]
<b>Explanation:</b>
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>The range of node's value is in the range of 32-bit signed integer.</li>
</ol>
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
const averageOfLevels = (root) => {
  
  const aux = (node, level, sums) => {
    if (!node) {
      return sums
    }
    if (node.left) {
      aux(node.left, level + 1, sums)
    }
    sums[level] = sums[level] ? {
      sum: sums[level].sum + node.val,
      counter: sums[level].counter + 1,
    } : {
      sum: node.val,
      counter: 1,
    }
    if (node.right) {
      aux(node.right, level + 1, sums)
    }
    return sums
  }
  const sums = aux(root, 0, [])
  return sums.map(({ sum, counter }) => sum / counter)
}
```
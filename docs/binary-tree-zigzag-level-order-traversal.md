---
id: binary-tree-zigzag-level-order-traversal
title: Binary Tree Zigzag Level Order Traversal
sidebar_label: Binary Tree Zigzag Level Order Traversal
---
## Description
<div class="description">
<p>Given a binary tree, return the <i>zigzag level order</i> traversal of its nodes' values. (ie, from left to right, then right to left for the next level and alternate between).</p>

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
return its zigzag level order traversal as:<br />
<pre>
[
  [3],
  [20,9],
  [15,7]
]
</pre>
</p>
</div>

## Solution
```javascript
/*
 * @lc app=leetcode id=103 lang=javascript
 *
 * [103] Binary Tree Zigzag Level Order Traversal
 *
 * https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/
 *
 * algorithms
 * Medium (39.92%)
 * Total Accepted:    191.3K
 * Total Submissions: 476.2K
 * Testcase Example:  '[3,9,20,null,null,15,7]'
 *
 * Given a binary tree, return the zigzag level order traversal of its nodes'
 * values. (ie, from left to right, then right to left for the next level and
 * alternate between).
 *
 *
 * For example:
 * Given binary tree [3,9,20,null,null,15,7],
 *
 * ⁠   3
 * ⁠  / \
 * ⁠ 9  20
 * ⁠   /  \
 * ⁠  15   7
 *
 *
 *
 * return its zigzag level order traversal as:
 *
 * [
 * ⁠ [3],
 * ⁠ [20,9],
 * ⁠ [15,7]
 * ]
 *
 *
 */
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
// iteration
const zigzagLevelOrder = (root) => {
  const result = []
  if (!root) {
    return result
  }
  let frontier = [root]
  result[0] = [root.val]
  let level = 0
  while (frontier.length) {
    const next = []
    level += 1
    frontier.forEach((node) => {
      if (node.left) {
        next.push(node.left)
      }
      if (node.right) {
        next.push(node.right)
      }
    })
    if (next.length !== 0) {
      result[level] = next.map(node => node.val)
    }
    frontier = next
  }
  return result.map((levels, index) => {
    if (index % 2 === 1) {
      return levels.reverse()
    }
    return levels
  })
}

```
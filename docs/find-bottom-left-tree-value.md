---
id: find-bottom-left-tree-value
title: Find Bottom Left Tree Value
sidebar_label: Find Bottom Left Tree Value
---
## Description
<div class="description">
<p>
Given a binary tree, find the leftmost value in the last row of the tree. 
</p>

<p><b>Example 1:</b><br />
<pre>
Input:

    2
   / \
  1   3

Output:
1
</pre>
</p>

<p> <b> Example 2: </b><br>
<pre>
Input:

        1
       / \
      2   3
     /   / \
    4   5   6
       /
      7

Output:
7
</pre>
</p>

<p><b>Note:</b>
You may assume the tree (i.e., the given root node) is not <b>NULL</b>.
</p>
</div>

## Solution(javascript)
```javascript
/*
 * @lc app=leetcode id=513 lang=javascript
 *
 * [513] Find Bottom Left Tree Value
 *
 * https://leetcode.com/problems/find-bottom-left-tree-value/description/
 *
 * algorithms
 * Medium (57.65%)
 * Total Accepted:    64.4K
 * Total Submissions: 111.3K
 * Testcase Example:  '[2,1,3]'
 *
 *
 * Given a binary tree, find the leftmost value in the last row of the tree.
 *
 *
 * Example 1:
 *
 * Input:
 *
 * ⁠   2
 * ⁠  / \
 * ⁠ 1   3
 *
 * Output:
 * 1
 *
 *
 *
 * ⁠ Example 2:
 *
 * Input:
 *
 * ⁠       1
 * ⁠      / \
 * ⁠     2   3
 * ⁠    /   / \
 * ⁠   4   5   6
 * ⁠      /
 * ⁠     7
 *
 * Output:
 * 7
 *
 *
 *
 * Note:
 * You may assume the tree (i.e., the given root node) is not NULL.
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
 * @return {number}
 */
const findBottomLeftValue = (root) => {
  let frontier = [root]
  let previous = frontier
  while (frontier.length) {
    const next = []
    frontier.forEach((node) => {
      if (node.left) {
        next.push(node.left)
      }
      if (node.right) {
        next.push(node.right)
      }
    })
    if (next.length !== 0) {
      previous = next
    }
    frontier = next
  }
  return previous[0].val
}

```
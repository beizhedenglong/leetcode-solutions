---
id: maximum-depth-of-n-ary-tree
title: Maximum Depth of N-ary Tree
sidebar_label: Maximum Depth of N-ary Tree
---
## Description
<div class="description">
<p>Given a n-ary tree, find its maximum depth.</p>

<p>The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.</p>

<p>For example, given a <code>3-ary</code> tree:</p>
&nbsp;

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;" /></p>

<p>&nbsp;</p>

<p>We should return its max depth, which is 3.</p>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>The depth of the tree is at most <code>1000</code>.</li>
	<li>The total number of nodes is at most <code>5000</code>.</li>
</ol>

</div>

## Solution
```javascript
/**
 * // Definition for a Node.
 * function Node(val,children) {
 *    this.val = val;
 *    this.children = children;
 * };
 */
/**
 * @param {Node} root
 * @return {number}
 */
// iteration
const maxDepth = (root) => {
  let max = 0
  if (!root) {
    return 0
  }
  let frontier = [root]
  while (frontier.length) {
    const next = []
    max += 1
    frontier.forEach((node) => {
      next.push(...node.children)
    })
    frontier = next
  }
  return max
}

```
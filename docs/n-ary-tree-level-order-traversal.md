---
id: n-ary-tree-level-order-traversal
title: N-ary Tree Level Order Traversal
sidebar_label: N-ary Tree Level Order Traversal
---
## Description
<div class="description">
<p>Given an n-ary tree, return the level order traversal of its nodes&#39; values. (ie, from left to right, level by level).</p>

<p>For example, given a <code>3-ary</code> tree:</p>

<p>&nbsp;</p>

<p><img src="https://assets.leetcode.com/uploads/2018/10/12/narytreeexample.png" style="width: 100%; max-width: 300px;" /></p>

<p>&nbsp;</p>

<p>We should return its level order traversal:</p>

<pre>
[
     [1],
     [3,2,4],
     [5,6]
]
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>The depth of the tree is at most <code>1000</code>.</li>
	<li>The total number of nodes is at most <code>5000</code>.</li>
</ol>

</div>

## Solution(javascript)
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
 * @return {number[][]}
 */
const levelOrder = (root) => {
  const res = []
  if (!root) {
    return res
  }
  let frontier = [root]
  while (frontier.length) {
    const next = []
    res.push(frontier.map(node => node.val))
    frontier.forEach((node) => {
      if (node.children) {
        next.push(...node.children)
      }
    })
    frontier = next
  }
  return res
}

```
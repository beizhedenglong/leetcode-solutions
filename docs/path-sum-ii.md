---
id: path-sum-ii
title: Path Sum II
sidebar_label: Path Sum II
---
## Description
<div class="description">
<p>Given a binary tree and a sum, find all root-to-leaf paths where each path&#39;s sum equals the given sum.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<p>Given the below binary tree and <code>sum = 22</code>,</p>

<pre>
      <strong>5</strong>
     <strong>/ \</strong>
    <strong>4   8</strong>
   <strong>/</strong>   / <strong>\</strong>
  <strong>11</strong>  13  <strong>4</strong>
 /  <strong>\</strong>    <strong>/</strong> \
7    <strong>2</strong>  <strong>5</strong>   1
</pre>

<p>Return:</p>

<pre>
[
   [5,4,11,2],
   [5,8,4,5]
]
</pre>

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
 * @param {number} sum
 * @return {boolean}
 */
const pathSum = (root, sum) => {
  const res = []
  const aux = (node, currentSum, acc) => {
    if (!node) {
      return
    }
    if (node && !node.left && !node.right) {
      if ((currentSum + node.val) === sum) {
        acc.push(node.val)
        res.push(acc)
      }
    }
    
    aux(node.left, currentSum + node.val, [...acc, node.val])
    aux(node.right, currentSum + node.val, [...acc, node.val])
  }
  if (root === null) {
    return res
  }
  aux(root, 0, [])
    return res
}

```
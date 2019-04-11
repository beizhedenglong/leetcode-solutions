---
id: path-sum
title: Path Sum
sidebar_label: Path Sum
---
## Description
<div class="description">
<p>Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<p>Given the below binary tree and <code>sum = 22</code>,</p>

<pre>
      <strong>5</strong>
     <strong>/</strong> \
    <strong>4</strong>   8
   <strong>/</strong>   / \
  <strong>11</strong>  13  4
 /  <strong>\</strong>      \
7    <strong>2</strong>      1
</pre>

<p>return true, as there exist a root-to-leaf path <code>5-&gt;4-&gt;11-&gt;2</code> which sum is 22.</p>

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
const hasPathSum = (root, sum) => {
  const aux = (node, currentSum) => {
    if (!node) {
      return false
    }
    if (node && !node.left && !node.right) {
      return (currentSum + node.val) === sum
    }
    const isLeftHas = aux(node.left, currentSum + node.val)
    const isRightHas = aux(node.right, currentSum + node.val)
    return (isLeftHas || isRightHas)
  }
  if (root === null) {
    return false
  }
  return aux(root, 0)
}

```
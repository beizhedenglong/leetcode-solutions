---
id: increasing-order-search-tree
title: Increasing Order Search Tree
sidebar_label: Increasing Order Search Tree
---
## Description
<div class="description">
<p>Given a tree, rearrange the tree in <strong>in-order</strong> so that the leftmost node in the tree is now the root of the tree, and every node has no left child and only 1 right child.</p>

<pre>
<strong>Example 1:</strong>
<strong>Input:</strong> [5,3,6,2,4,null,8,1,null,null,null,7,9]

       5
      / \
    3    6
   / \    \
  2   4    8
&nbsp;/        / \ 
1        7   9

<strong>Output:</strong> [1,null,2,null,3,null,4,null,5,null,6,null,7,null,8,null,9]

 1
&nbsp; \
&nbsp;  2
&nbsp;   \
&nbsp;    3
&nbsp;     \
&nbsp;      4
&nbsp;       \
&nbsp;        5
&nbsp;         \
&nbsp;          6
&nbsp;           \
&nbsp;            7
&nbsp;             \
&nbsp;              8
&nbsp;               \
                 9  </pre>

<p><strong>Note:</strong></p>

<ol>
	<li>The number of nodes in the given tree will be between 1 and 100.</li>
	<li>Each node will have a unique integer value from 0 to 1000.</li>
</ol>

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
 * @return {TreeNode}
 */
const increasingBST = (root) => {
  const vals = []
  const aux = (node) => {
    if (!node) {
      return
    }
    if (node.left) {
      aux(node.left)
    }
    vals.push({ val: node.val, left: null, right: null })
    if (node.right) {
      aux(node.right)
    }
  }
  aux(root)
  for (let i = 0; i < vals.length - 1; i++) {
    vals[i].right = vals[i + 1]
  }
  return vals[0]
}

```
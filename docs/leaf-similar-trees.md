---
id: leaf-similar-trees
title: Leaf-Similar Trees
sidebar_label: Leaf-Similar Trees
---
## Description
<div class="description">
<p>Consider all the leaves of a binary tree.&nbsp; From&nbsp;left to right order, the values of those&nbsp;leaves form a <em>leaf value sequence.</em></p>

<p><img alt="" src="https://s3-lc-upload.s3.amazonaws.com/uploads/2018/07/16/tree.png" style="width: 300px; height: 240px;" /></p>

<p>For example, in the given tree above, the leaf value sequence is <code>(6, 7, 4, 9, 8)</code>.</p>

<p>Two binary trees are considered <em>leaf-similar</em>&nbsp;if their leaf value sequence is the same.</p>

<p>Return <code>true</code> if and only if the two given trees with head nodes <code>root1</code> and <code>root2</code> are leaf-similar.</p>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ul>
	<li>Both of the given trees will have between <code>1</code> and <code>100</code> nodes.</li>
</ul>

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
 * @param {TreeNode} root1
 * @param {TreeNode} root2
 * @return {boolean}
 */
const leafSimilar = (root1, root2) => {
  const traverse = (node, leaves) => {
    if (!node) {
      return leaves
    }
    if (node.left) {
      leaves.push(...traverse(node.left, []))
    }
    if (!node.left && !node.right) {
      leaves.push(node.val)
    }
    if (node.right) {
      leaves.push(...traverse(node.right, []))
    }
    return leaves
  }
  const leaves1 = traverse(root1, [])
  const leaves2 = traverse(root2, [])
  return leaves1.every((l1, index) => l1 === leaves2[index])
}
```
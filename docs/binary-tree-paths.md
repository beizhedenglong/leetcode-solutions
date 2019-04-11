---
id: binary-tree-paths
title: Binary Tree Paths
sidebar_label: Binary Tree Paths
---
## Description
<div class="description">
<p>Given a binary tree, return all root-to-leaf paths.</p>

<p><strong>Note:</strong>&nbsp;A leaf is a node with no children.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>

   1
 /   \
2     3
 \
  5

<strong>Output:</strong> [&quot;1-&gt;2-&gt;5&quot;, &quot;1-&gt;3&quot;]

<strong>Explanation:</strong> All root-to-leaf paths are: 1-&gt;2-&gt;5, 1-&gt;3
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
 * @return {string[]}
 */
const binaryTreePaths = (root) => {
  const isLeaf = node => node && (!node.left) && (!node.right)
  const join = (current, val) => (current ? `${current}->${val}` : `${val}`)
  const aux = (node, currentPath = '', acc) => {
    if (!node) {
      return acc
    }
    if (isLeaf(node)) {
      currentPath = join(currentPath, node.val)
      acc.push(currentPath)
    }
    aux(node.left, join(currentPath, node.val), acc)
    aux(node.right, join(currentPath, node.val), acc)
    return acc
  }
  return aux(root, '', [])
}

```
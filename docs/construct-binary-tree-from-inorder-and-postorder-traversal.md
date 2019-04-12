---
id: construct-binary-tree-from-inorder-and-postorder-traversal
title: Construct Binary Tree from Inorder and Postorder Traversal
sidebar_label: Construct Binary Tree from Inorder and Postorder Traversal
---
## Description
<div class="description">
<p>Given inorder and postorder traversal of a tree, construct the binary tree.</p>

<p><strong>Note:</strong><br />
You may assume that duplicates do not exist in the tree.</p>

<p>For example, given</p>

<pre>
inorder =&nbsp;[9,3,15,20,7]
postorder = [9,15,7,20,3]</pre>

<p>Return the following binary tree:</p>

<pre>
    3
   / \
  9  20
    /  \
   15   7
</pre>

</div>

## Solution(javascript)
```javascript

const buildTree = (inorder, postorder) => {
  if (postorder.length === 0) {
    return null
  }

  const node = {
    val: postorder[postorder.length - 1],
    left: null,
    right: null,
  }
  const index = inorder.findIndex(v => v === postorder[postorder.length - 1])
  const rightCount = inorder.length - 1 - index

  node.right = buildTree(
    inorder.slice(index + 1),
    postorder.slice(inorder.length - 1 - rightCount, inorder.length - 1),
  )
  node.left = buildTree(
    inorder.slice(0, index),
    postorder.slice(0, inorder.length - 1 - rightCount),
  )
  return node
}

```
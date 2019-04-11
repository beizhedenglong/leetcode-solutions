---
id: insert-into-a-binary-search-tree
title: Insert into a Binary Search Tree
sidebar_label: Insert into a Binary Search Tree
---
## Description
<div class="description">
<p>Given the root node of a binary search tree (BST) and a value to be inserted into the tree,&nbsp;insert the value into the BST. Return the root node of the BST after the insertion. It is guaranteed that the new value does not exist in the original BST.</p>

<p>Note that there may exist&nbsp;multiple valid ways for the&nbsp;insertion, as long as the tree remains a BST after insertion. You can return any of them.</p>

<p>For example,&nbsp;</p>

<pre>
Given the tree:
        4
       / \
      2   7
     / \
    1   3
And the value to insert: 5
</pre>

<p>You can return this binary search tree:</p>

<pre>
         4
       /   \
      2     7
     / \   /
    1   3 5
</pre>

<p>This tree is also valid:</p>

<pre>
         5
       /   \
      2     7
     / \   
    1   3
         \
          4
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
 * @param {number} val
 * @return {TreeNode}
 */
const insertIntoBST = (root, val) => {
  const aux = (node) => {
    if (!node) {
      return root
    }
    if (val >= node.val && !node.right) {
      node.right = {
        val,
        left: null,
        right: null,
      }
      return root
    }
    if (val <= node.val && !node.left) {
      node.left = {
        val,
        left: null,
        right: null,
      }
      return root
    }
    if (val >= node.val) {
      return aux(node.right)
    }
    return aux(node.left)
  }
  return aux(root)
}

```
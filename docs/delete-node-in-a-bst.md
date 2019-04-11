---
id: delete-node-in-a-bst
title: Delete Node in a BST
sidebar_label: Delete Node in a BST
---
## Description
<div class="description">
<p>Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return the root node reference (possibly updated) of the BST.</p>

<p>Basically, the deletion can be divided into two stages:
<ol>
<li>Search for a node to remove.</li>
<li>If the node is found, delete the node.</li>
</ol>
</p>

<p><b>Note:</b> Time complexity should be O(height of tree).</p>

<p><b>Example:</b>
<pre>
root = [5,3,6,2,4,null,7]
key = 3

    5
   / \
  3   6
 / \   \
2   4   7

Given key to delete is 3. So we find the node with value 3 and delete it.

One valid answer is [5,4,6,2,null,null,7], shown in the following BST.

    5
   / \
  4   6
 /     \
2       7

Another valid answer is [5,2,6,null,4,null,7].

    5
   / \
  2   6
   \   \
    4   7
</pre>
</p>
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
 * @param {number} key
 * @return {TreeNode}
 */

const deleteNode = (root, key) => {
  if (!root) {
    return null
  }
  if (root.val === key) {
    if (!root.left || !root.right) {
      return root.left || root.right
    }
    let nextLarger = root.right
    while (nextLarger && nextLarger.left) {
      nextLarger = nextLarger.left
    }
    nextLarger.left = root.left
    return root.right
  }
  if (root.val < key) {
    root.right = deleteNode(root.right, key)
  }
  if (root.val > key) {
    root.left = deleteNode(root.left, key)
  }
  return root
}

```
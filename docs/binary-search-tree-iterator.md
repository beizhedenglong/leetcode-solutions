---
id: binary-search-tree-iterator
title: Binary Search Tree Iterator
sidebar_label: Binary Search Tree Iterator
---
## Description
<div class="description">
<p>Implement an iterator over a binary search tree (BST). Your iterator will be initialized with the root node of a BST.</p>

<p>Calling <code>next()</code> will return the next smallest number in the BST.</p>

<p>&nbsp;</p>

<ul>
</ul>

<p><strong>Example:</strong></p>

<p><strong><img alt="" src="https://assets.leetcode.com/uploads/2018/12/25/bst-tree.png" style="width: 189px; height: 178px;" /></strong></p>

<pre>
BSTIterator iterator = new BSTIterator(root);
iterator.next();    // return 3
iterator.next();    // return 7
iterator.hasNext(); // return true
iterator.next();    // return 9
iterator.hasNext(); // return true
iterator.next();    // return 15
iterator.hasNext(); // return true
iterator.next();    // return 20
iterator.hasNext(); // return false
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ul>
	<li><code>next()</code> and <code>hasNext()</code> should run in average O(1) time and uses O(<i>h</i>) memory, where <i>h</i> is the height of the tree.</li>
	<li>You may assume that&nbsp;<code>next()</code>&nbsp;call&nbsp;will always be valid, that is, there will be at least a next smallest number in the BST when <code>next()</code> is called.</li>
</ul>

</div>

## Solution(javascript)
```javascript
// https://leetcode.com/problems/binary-tree-inorder-traversal/submissions/


/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 */
const BSTIterator = function (root) {
  const traverse = (node, acc = []) => {
    if (node) {
      traverse(node.left, acc)
      acc.push(node.val)
      traverse(node.right, acc)
    }
    return acc
  }
  this.values = traverse(root)
  this.counter = 0
}

/**
 * @return the next smallest number
 * @return {number}
 */
BSTIterator.prototype.next = function () {
  const v = this.values[this.counter]
  this.counter++
  return v
}

/**
 * @return whether we have a next smallest number
 * @return {boolean}
 */
BSTIterator.prototype.hasNext = function () {
  return this.counter <= this.values.length - 1
}

/**
 * Your BSTIterator object will be instantiated and called as such:
 * var obj = Object.create(BSTIterator).createNew(root)
 * var param_1 = obj.next()
 * var param_2 = obj.hasNext()
 */

```
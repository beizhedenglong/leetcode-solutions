---
id: convert-sorted-list-to-binary-search-tree
title: Convert Sorted List to Binary Search Tree
sidebar_label: Convert Sorted List to Binary Search Tree
---
## Description
<div class="description">
<p>Given a singly linked list where elements are sorted in ascending order, convert it to a height balanced BST.</p>

<p>For this problem, a height-balanced binary tree is defined as a binary tree in which the depth of the two subtrees of <em>every</em> node never differ by more than 1.</p>

<p><strong>Example:</strong></p>

<pre>
Given the sorted linked list: [-10,-3,0,5,9],

One possible answer is: [0,-3,9,-10,null,5], which represents the following height balanced BST:

      0
     / \
   -3   9
   /   /
 -10  5
</pre>

</div>

## Solution
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {TreeNode}
 */
const sortedListToBST = function (head) {
  const nodes = []
  while (head) {
    head.left = null
    head.right = null
    nodes.push(head)
    head = head.next
  }
  const aux = (nodes, low, high) => { // eslint-disable-line
    if (low > high) {
      return null
    }
    const middle = Math.floor((low + high) / 2)
    nodes[middle].left = aux(nodes, low, middle - 1)
    nodes[middle].right = aux(nodes, middle + 1, high)
    return nodes[middle]
  }
  return aux(nodes, 0, nodes.length - 1)
}

```
---
id: maximum-binary-tree
title: Maximum Binary Tree
sidebar_label: Maximum Binary Tree
---
## Description
<div class="description">
<p>
Given an integer array with no duplicates. A maximum tree building on this array is defined as follow:
<ol>
<li>The root is the maximum number in the array. </li>
<li>The left subtree is the maximum tree constructed from left part subarray divided by the maximum number.</li>
<li>The right subtree is the maximum tree constructed from right part subarray divided by the maximum number.</li> 
</ol>
</p>

<p>
Construct the maximum tree by the given array and output the root node of this tree.
</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> [3,2,1,6,0,5]
<b>Output:</b> return the tree root node representing the following tree:

      6
    /   \
   3     5
    \    / 
     2  0   
       \
        1
</pre>
</p>

<p><b>Note:</b><br>
<ol>
<li>The size of the given array will be in the range [1,1000].</li>
</ol>
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
 * @param {number[]} nums
 * @return {TreeNode}
 */
const constructMaximumBinaryTree = (nums) => {
  if (!nums.length) {
    return null
  }
  const maxIndex = (low, high) => {
    let max = low
    for (let i = low; i <= high; i++) {
      if (nums[i] > nums[max]) {
        max = i
      }
    }
    return max
  }
  const treeNode = () => ({
    val: null,
    left: null,
    right: null,
  })
  const aux = (node, low, high) => {
    if (low > high) {
      return null
    }
    const currentMaxIndex = maxIndex(low, high)
    node.val = nums[currentMaxIndex]
    node.right = aux(treeNode(), currentMaxIndex + 1, high)
    node.left = aux(treeNode(), low, currentMaxIndex - 1)
    return node
  }
  const root = treeNode()
  aux(root, 0, nums.length - 1)
  return root
}

```
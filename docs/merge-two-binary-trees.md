---
id: merge-two-binary-trees
title: Merge Two Binary Trees
sidebar_label: Merge Two Binary Trees
---
## Description
<div class="description">
<p>Given two binary trees and imagine that when you put one of them to cover the other, some nodes of the two trees are overlapped while the others are not.</p>

<p>You need to merge them into a new binary tree. The merge rule is that if two nodes overlap, then sum node values up as the new value of the merged node. Otherwise, the NOT null node will be used as the node of new tree.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
<b>Output:</b> 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
</pre>

<p>&nbsp;</p>

<p><b>Note:</b> The merging process must start from the root nodes of both trees.</p>

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
 * @param {TreeNode} t1
 * @param {TreeNode} t2
 * @return {TreeNode}
 */
const mergeTrees = (t1, t2) => {
  if (!t1) {
    return t2
  }
  if (!t2) {
    return t1
  }
  t1.val += t2.val
  t1.left = mergeTrees(t1.left, t2.left)
  t1.right = mergeTrees(t1.right, t2.right)
    return t1
}
```
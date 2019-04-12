---
id: binary-tree-right-side-view
title: Binary Tree Right Side View
sidebar_label: Binary Tree Right Side View
---
## Description
<div class="description">
<p>Given a binary tree, imagine yourself standing on the <em>right</em> side of it, return the values of the nodes you can see ordered from top to bottom.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>&nbsp;[1,2,3,null,5,null,4]
<strong>Output:</strong>&nbsp;[1, 3, 4]
<strong>Explanation:
</strong>
   1            &lt;---
 /   \
2     3         &lt;---
 \     \
  5     4       &lt;---
</pre>
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
 * @return {number[]}
 */
const rightSideView = (root) => {
  let frontier = [root]
  const res =  []
  while (frontier.length) {
    if(frontier[frontier.length - 1]) {
        res.push(frontier[frontier.length - 1].val)   
    }

    frontier = frontier.reduce((next, node) => {
        if(!node) {
            return next
        }
      if (node.left) {
        next.push(node.left)
      }
      if (node.right) {
        next.push(node.right)
      }
      return next
    }, [])
  }
  return res
}

```
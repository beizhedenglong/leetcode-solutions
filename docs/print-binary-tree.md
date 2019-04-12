---
id: print-binary-tree
title: Print Binary Tree
sidebar_label: Print Binary Tree
---
## Description
<div class="description">
<p>Print a binary tree in an m*n 2D string array following these rules: </p>

<ol>
<li>The row number <code>m</code> should be equal to the height of the given binary tree.</li>
<li>The column number <code>n</code> should always be an odd number.</li>
<li>The root node's value (in string format) should be put in the exactly middle of the first row it can be put. The column and the row where the root node belongs will separate the rest space into two parts (<b>left-bottom part and right-bottom part</b>). You should print the left subtree in the left-bottom part and print the right subtree in the right-bottom part. The left-bottom part and the right-bottom part should have the same size. Even if one subtree is none while the other is not, you don't need to print anything for the none subtree but still need to leave the space as large as that for the other subtree. However, if two subtrees are none, then you don't need to leave space for both of them. </li>
<li>Each unused space should contain an empty string <code>""</code>.</li>
<li>Print the subtrees following the same rules.</li>
</ol>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b>
     1
    /
   2
<b>Output:</b>
[["", "1", ""],
 ["2", "", ""]]
</pre>
</p>


<p><b>Example 2:</b><br />
<pre>
<b>Input:</b>
     1
    / \
   2   3
    \
     4
<b>Output:</b>
[["", "", "", "1", "", "", ""],
 ["", "2", "", "", "", "3", ""],
 ["", "", "4", "", "", "", ""]]
</pre>
</p>

<p><b>Example 3:</b><br />
<pre>
<b>Input:</b>
      1
     / \
    2   5
   / 
  3 
 / 
4 
<b>Output:</b>

[["",  "",  "", "",  "", "", "", "1", "",  "",  "",  "",  "", "", ""]
 ["",  "",  "", "2", "", "", "", "",  "",  "",  "",  "5", "", "", ""]
 ["",  "3", "", "",  "", "", "", "",  "",  "",  "",  "",  "", "", ""]
 ["4", "",  "", "",  "", "", "", "",  "",  "",  "",  "",  "", "", ""]]
</pre>
</p>

<p><b>Note:</b>
The height of binary tree is in the range of [1, 10].
</p>
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
 * @return {string[][]}
 */
const getHeight = (node, currentHeight = 0) => {
  if (!node) {
    return currentHeight
  }
  const leftHeight = getHeight(node.left, currentHeight + 1)
  const rightHeight = getHeight(node.right, currentHeight + 1)
  return leftHeight > rightHeight ? leftHeight : rightHeight
}
const fill = (node, rowIndex, left, right, res = []) => {
  if (!node) {
    return res
  }

  const columnIndex = Math.floor((left + right) / 2)
  res[rowIndex][columnIndex] = `${node.val}`
  fill(node.left, rowIndex + 1, left, columnIndex - 1, res)
  fill(node.right, rowIndex + 1, columnIndex + 1, right, res)
  return res
}
const printTree = function (root) {
  const treeHeight = getHeight(root)
  const columnNum = (2 ** treeHeight) - 1
  const getRow = () => new Array(columnNum).fill('')
  const res = new Array(treeHeight).fill('').map(getRow)
  return fill(root, 0, 0, columnNum - 1, res)
}

```
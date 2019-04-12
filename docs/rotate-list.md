---
id: rotate-list
title: Rotate List
sidebar_label: Rotate List
---
## Description
<div class="description">
<p>Given a linked&nbsp;list, rotate the list to the right by <em>k</em> places, where <em>k</em> is non-negative.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL, k = 2
<strong>Output:</strong> 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL
<strong>Explanation:</strong>
rotate 1 steps to the right: 5-&gt;1-&gt;2-&gt;3-&gt;4-&gt;NULL
rotate 2 steps to the right: 4-&gt;5-&gt;1-&gt;2-&gt;3-&gt;NULL
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 0-&gt;1-&gt;2-&gt;NULL, k = 4
<strong>Output:</strong> <code>2-&gt;0-&gt;1-&gt;NULL</code>
<strong>Explanation:</strong>
rotate 1 steps to the right: 2-&gt;0-&gt;1-&gt;NULL
rotate 2 steps to the right: 1-&gt;2-&gt;0-&gt;NULL
rotate 3 steps to the right:&nbsp;<code>0-&gt;1-&gt;2-&gt;NULL</code>
rotate 4 steps to the right:&nbsp;<code>2-&gt;0-&gt;1-&gt;NULL</code></pre>

</div>

## Solution(javascript)
```javascript


const rotate = function (nums, k) {
  while (k > 0) {
    nums.unshift(nums.pop())
    k--
  }
  return nums
}

const rotateRight = function (head, k) {
  if (!head) {
    return head
  }
  const list = []
  let current = head
  while (current) {
    list.push(current)
    current = current.next
  }
  rotate(list, k % list.length)
    .forEach((node, index) => { node.next = list[index + 1] ? list[index + 1] : null })
  return list[0]
}

```
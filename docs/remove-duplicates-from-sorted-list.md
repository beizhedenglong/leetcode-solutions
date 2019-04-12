---
id: remove-duplicates-from-sorted-list
title: Remove Duplicates from Sorted List
sidebar_label: Remove Duplicates from Sorted List
---
## Description
<div class="description">
<p>Given a sorted linked list, delete all duplicates such that each element appear only <em>once</em>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;1-&gt;2
<strong>Output:</strong> 1-&gt;2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;1-&gt;2-&gt;3-&gt;3
<strong>Output:</strong> 1-&gt;2-&gt;3
</pre>

</div>

## Solution(javascript)
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
const deleteDuplicates = (head) => {
  const aux = (current) => {
    if (!current || !current.next) {
      return head
    }
    if (current.val === current.next.val) {
      current.next = current.next.next
        return aux(current)
    }
    return aux(current.next)
  }
  return aux(head)
}
```
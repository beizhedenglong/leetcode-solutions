---
id: merge-two-sorted-lists
title: Merge Two Sorted Lists
sidebar_label: Merge Two Sorted Lists
---
## Description
<div class="description">
<p>Merge two sorted linked lists and return it as a new list. The new list should be made by splicing together the nodes of the first two lists.</p>

<p><b>Example:</b>
<pre>
<b>Input:</b> 1->2->4, 1->3->4
<b>Output:</b> 1->1->2->3->4->4
</pre>
</p>
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
 * @param {ListNode} l1
 * @param {ListNode} l2
 * @return {ListNode}
 */
const mergeTwoLists = (l1, l2) => {
  const aux = (current1, current2, acc) => {
    if (!current1) {
      acc.next = current2
      return acc
    }
    if (!current2) {
      acc.next = current1
      return acc
    }
    if (current1.val < current2.val) {
      acc.next = {
        val: current1.val,
        next: null,
      }
      return aux(current1.next, current2, acc.next)
    }
    acc.next = {
      val: current2.val,
      next: null,
    }
    return aux(current2.next, current1, acc.next)
  }
  const head = { val: null, next: null }
  aux(l1, l2, head)
    return head.next
}

```
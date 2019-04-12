---
id: reverse-linked-list
title: Reverse Linked List
sidebar_label: Reverse Linked List
---
## Description
<div class="description">
<p>Reverse a singly linked list.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;3-&gt;4-&gt;5-&gt;NULL
<strong>Output:</strong> 5-&gt;4-&gt;3-&gt;2-&gt;1-&gt;NULL
</pre>

<p><b>Follow up:</b></p>

<p>A linked list can be reversed either iteratively or recursively. Could you implement both?</p>

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
// const reverseList = (head) => {
//   if (!head) {
//     return head
//   }
//   let returned = { val: head.val, next: null }
//   let current = head
//   while (current.next) {
//     current = current.next
//     returned = {
//       val: current.val,
//       next: returned,
//     }
//   }
//   return returned
// }

const reverseList = (head) => {
  const aux = (current, acc) => {
    if (!current) {
      return acc
    }
    return aux(current.next, {
      val: current.val,
      next: acc,
    })
  }
  return aux(head, null)
}
```
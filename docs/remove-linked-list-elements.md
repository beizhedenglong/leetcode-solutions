---
id: remove-linked-list-elements
title: Remove Linked List Elements
sidebar_label: Remove Linked List Elements
---
## Description
<div class="description">
<p>Remove all elements from a linked list of integers that have value <b><i>val</i></b>.</p>

<p><b>Example:</b></p>

<pre>
<b>Input:</b>  1-&gt;2-&gt;6-&gt;3-&gt;4-&gt;5-&gt;6, <em><b>val</b></em> = 6
<b>Output:</b> 1-&gt;2-&gt;3-&gt;4-&gt;5
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
 * @param {ListNode} head
 * @param {number} val
 * @return {ListNode}
 */
// const removeElements = (head, val) => {
//   const aux = (current, acc) => {
//     if (!current) {
//       return acc
//     }
//     if (current.val === val) {
//       return aux(current.next, acc)
//     }
//     acc.next = {
//       val: current.val,
//       next: null,
//     }
//     return aux(current.next, acc.next)
//   }
//   const initial = { val: null, next: null }
//   aux(head, initial)
//     return initial.next
// }

const removeElements = (head, val) => {
  if (!head) {
    return head
  }
  if (head.val === val) {
    return removeElements(head.next, val)
  }
  head.next = removeElements(head.next, val)
  return head
}
```
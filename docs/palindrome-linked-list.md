---
id: palindrome-linked-list
title: Palindrome Linked List
sidebar_label: Palindrome Linked List
---
## Description
<div class="description">
<p>Given a singly linked list, determine if it is a palindrome.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2
<strong>Output:</strong> false</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 1-&gt;2-&gt;2-&gt;1
<strong>Output:</strong> true</pre>

<p><b>Follow up:</b><br />
Could you do it in O(n) time and O(1) space?</p>

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
 * @return {boolean}
 */
const isPalindrome = (head) => {
  const reverse = (head) => {
    const aux = (current, acc) => {
      if (!current) {
        return acc
      }
      acc = {
        val: current.val,
        next: acc,
      }
      return aux(current.next, acc)
    }
    return aux(head, null)
  }
  const reversed = reverse(head)
  const compare = (c1, c2) => {
    if (!c1) {
      return true
    }
    if (c1.val === c2.val) {
      return compare(c1.next, c2.next)
    }
    return false
  }
  return compare(head, reversed)
}
```
---
id: middle-of-the-linked-list
title: Middle of the Linked List
sidebar_label: Middle of the Linked List
---
## Description
<div class="description">
<p>Given a non-empty, singly&nbsp;linked list with head node <code>head</code>, return&nbsp;a&nbsp;middle node of linked list.</p>

<p>If there are two middle nodes, return the second middle node.</p>

<p>&nbsp;</p>

<div>
<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-1-1">[1,2,3,4,5]</span>
<strong>Output: </strong>Node 3 from this list (Serialization: <span id="example-output-1">[3,4,5]</span>)
The returned node has value 3.  (The judge&#39;s serialization of this node is [3,4,5]).
Note that we returned a ListNode object ans, such that:
ans.val = 3, ans.next.val = 4, ans.next.next.val = 5, and ans.next.next.next = NULL.
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">[1,2,3,4,5,6]</span>
<strong>Output: </strong>Node 4 from this list (Serialization: <span id="example-output-2">[4,5,6]</span>)
Since the list has two middle nodes with values 3 and 4, we return the second one.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<ul>
	<li>The number of nodes in the given list will be between <code>1</code>&nbsp;and <code>100</code>.</li>
</ul>
</div>
</div>

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
const middleNode = (head) => {
  const aux = (current, acc) => {
    if (!current) {
      return acc
    }
    // performance concern
    acc.push(current)
    return aux(current.next, acc)
  }
  const res = aux(head, [])
  const middle = Math.floor(res.length / 2)
  return res[middle]
};
```
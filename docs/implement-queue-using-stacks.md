---
id: implement-queue-using-stacks
title: Implement Queue using Stacks
sidebar_label: Implement Queue using Stacks
---
## Description
<div class="description">
<p>Implement the following operations of a queue using stacks.</p>

<ul>
	<li>push(x) -- Push element x to the back of queue.</li>
	<li>pop() -- Removes the element from in front of queue.</li>
	<li>peek() -- Get the front element.</li>
	<li>empty() -- Return whether the queue is empty.</li>
</ul>

<p><b>Example:</b></p>

<pre>
MyQueue queue = new MyQueue();

queue.push(1);
queue.push(2);  
queue.peek();  // returns 1
queue.pop();   // returns 1
queue.empty(); // returns false</pre>

<p><b>Notes:</b></p>

<ul>
	<li>You must use <i>only</i> standard operations of a stack -- which means only <code>push to top</code>, <code>peek/pop from top</code>, <code>size</code>, and <code>is empty</code> operations are valid.</li>
	<li>Depending on your language, stack may not be supported natively. You may simulate a stack by using a list or deque (double-ended queue), as long as you use only standard operations of a stack.</li>
	<li>You may assume that all operations are valid (for example, no pop or peek operations will be called on an empty queue).</li>
</ul>

</div>

## Solution
```javascript
const Stack = function () {
  const stack = []
  return {
    get length() { return stack.length },
    push: x => stack.push(x),
    pop: () => stack.pop(),
    peek: () => stack[stack.length - 1],
  }
}


const MyQueue = function () {
  this.s1 = Stack()
  this.s2 = Stack()
}

/**
 * Push element x to the back of queue.
 * @param {number} x
 * @return {void}
 */
MyQueue.prototype.push = function (x) {
  this.s2.push(x)
}

/**
 * Removes the element from in front of queue and returns that element.
 * @return {number}
 */
MyQueue.prototype.pop = function () {
  if (this.s1.length) {
    return this.s1.pop()
  }
  while (this.s2.length) {
    this.s1.push(this.s2.pop())
  }
  return this.s1.pop()
}

/**
 * Get the front element.
 * @return {number}
 */
MyQueue.prototype.peek = function () {
  if (this.s1.length) {
    return this.s1.peek()
  }
  while (this.s2.length) {
    this.s1.push(this.s2.pop())
  }
  return this.s1.peek()
}

/**
 * Returns whether the queue is empty.
 * @return {boolean}
 */
MyQueue.prototype.empty = function () {
  return this.s1.length === 0 && this.s2.length === 0
}

```
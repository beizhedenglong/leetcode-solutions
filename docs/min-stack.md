---
id: min-stack
title: Min Stack
sidebar_label: Min Stack
---
## Description
<div class="description">
<p>
Design a stack that supports push, pop, top, and retrieving the minimum element in constant time.
<ul>
<li>
push(x) -- Push element x onto stack.
</li>
<li>
pop() -- Removes the element on top of the stack.
</li>
<li>
top() -- Get the top element.
</li>
<li>
getMin() -- Retrieve the minimum element in the stack.
</li>
</ul>
</p>

<p><b>Example:</b><br />
<pre>
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> Returns -3.
minStack.pop();
minStack.top();      --> Returns 0.
minStack.getMin();   --> Returns -2.
</pre>
</p>
</div>

## Solution(javascript)
```javascript
/**
 * initialize your data structure here.
 */
const MinStack = function () {
  this.stack = []
}

/**
 * @param {number} x
 * @return {void}
 */
MinStack.prototype.push = function (x) {
  if (this.stack.length === 0) {
    this.stack.push({
      val: x,
      min: x,
    })
  } else if (x < this.getMin()) {
    this.stack.push({
      val: x,
      min: x,
    })
  } else {
    this.stack.push({
      val: x,
      min: this.getMin(),
    })
  }
}

/**
 * @return {void}
 */
MinStack.prototype.pop = function () {
  this.stack.pop()
}

/**
 * @return {number}
 */
MinStack.prototype.top = function () {
  return this.stack.length === 0
    ? null
    : this.stack[this.stack.length - 1].val
}

/**
 * @return {number}
 */
MinStack.prototype.getMin = function () {
  return this.stack.length === 0
    ? null
    : this.stack[this.stack.length - 1].min
}

```
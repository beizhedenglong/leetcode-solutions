---
id: fibonacci-number
title: Fibonacci Number
sidebar_label: Fibonacci Number
---
## Description
<div class="description">
<p>The&nbsp;<b>Fibonacci numbers</b>, commonly denoted&nbsp;<code>F(n)</code>&nbsp;form a sequence, called the&nbsp;<b>Fibonacci sequence</b>, such that each number is the sum of the two preceding ones, starting from <code>0</code> and <code>1</code>. That is,</p>

<pre>
F(0) = 0,&nbsp; &nbsp;F(1)&nbsp;= 1
F(N) = F(N - 1) + F(N - 2), for N &gt; 1.
</pre>

<p>Given <code>N</code>, calculate <code>F(N)</code>.</p>

<p>&nbsp;</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 2
<strong>Output:</strong> 1
<strong>Explanation:</strong> F(2) = F(1) + F(0) = 1 + 0 = 1.
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 3
<strong>Output:</strong> 2
<strong>Explanation:</strong> F(3) = F(2) + F(1) = 1 + 1 = 2.
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 4
<strong>Output:</strong> 3
<strong>Explanation:</strong> F(4) = F(3) + F(2) = 2 + 1 = 3.
</pre>

<p>&nbsp;</p>

<p><strong>Note:</strong></p>

<p>0 &le; <code>N</code> &le; 30.</p>

</div>

## Solution
```javascript
/**
 * @param {number} N
 * @return {number}
 */
const fib = (N) => {
  if (N <= 1) {
    return N
  }
  const aux = (counter, prev, current) => {
    if (counter >= N) {
      return current
    }
    return aux(counter + 1, current, prev + current)
  }
  return aux(1, 0, 1)
}
```
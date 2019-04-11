---
id: valid-perfect-square
title: Valid Perfect Square
sidebar_label: Valid Perfect Square
---
## Description
<div class="description">
<p>Given a positive integer <i>num</i>, write a function which returns True if <i>num</i> is a perfect square else False.</p>

<p><b>Note:</b> <b>Do not</b> use any built-in library function such as <code>sqrt</code>.</p>

<p><strong>Example 1:</strong></p>

<div>
<pre>
<strong>Input: </strong><span id="example-input-1-1">16</span>
<strong>Output: </strong><span id="example-output-1">true</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong><span id="example-input-2-1">14</span>
<strong>Output: </strong><span id="example-output-2">false</span>
</pre>
</div>
</div>
</div>

## Solution
```javascript
/**
 * @param {number} num
 * @return {boolean}
 */
var isPerfectSquare = function(x) {
    let r = x
  while (r * r > x) {
    r = Math.floor((r + x / r) / 2)
  }

  return r * r === x
};
```
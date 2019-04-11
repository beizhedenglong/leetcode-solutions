---
id: add-binary
title: Add Binary
sidebar_label: Add Binary
---
## Description
<div class="description">
<p>Given two binary strings, return their sum (also a binary string).</p>

<p>The input strings are both <strong>non-empty</strong> and contains only characters <code>1</code> or&nbsp;<code>0</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;11&quot;, b = &quot;1&quot;
<strong>Output:</strong> &quot;100&quot;</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> a = &quot;1010&quot;, b = &quot;1011&quot;
<strong>Output:</strong> &quot;10101&quot;</pre>

</div>

## Solution
```javascript
/**
 * @param {string} a
 * @param {string} b
 * @return {string}
 */
const addBinary = function (a, b) {
  const reverse = x => x.split('').reverse()
  const { shorter, longer } = a.length > b.length
    ? { shorter: reverse(b), longer: reverse(a) }
    : { shorter: reverse(a), longer: reverse(b) }

  let reminder = 0
  const digits = longer.map((num1, index) => {
    let res = parseInt(num1, 10) + reminder
      + (parseInt(shorter[index], 10) ? parseInt(shorter[index], 10) : 0)
    if (res >= 2) {
      res -= 2
      reminder = 1
    } else {
      reminder = 0
    }
    return res
  })
  if (reminder === 1) {
    digits.push(reminder)
  }
  return digits.reverse().join('')
}

```
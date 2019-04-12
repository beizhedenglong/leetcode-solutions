---
id: repeated-string-match
title: Repeated String Match
sidebar_label: Repeated String Match
---
## Description
<div class="description">
<p>Given two strings A and B, find the minimum number of times A has to be repeated such that B is a substring of it. If no such solution, return -1.</p>

<p>For example, with A = &quot;abcd&quot; and B = &quot;cdabcdab&quot;.</p>

<p>Return 3, because by repeating A three times (&ldquo;abcdabcdabcd&rdquo;), B is a substring of it; and B is not a substring of A repeated two times (&quot;abcdabcd&quot;).</p>

<p><b>Note:</b><br />
The length of <code>A</code> and <code>B</code> will be between 1 and 10000.</p>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string} A
 * @param {string} B
 * @return {number}
 */
const repeatedStringMatch = function (A, B) {
  let i = 1
  let current = A
  while (true) {
    if (current.indexOf(B) >= 0) {
      return i
    }
    if ((current.length > B.length * 2) && i > 2) {
      return -1
    }
    current += A
    i += 1
  }
}

```
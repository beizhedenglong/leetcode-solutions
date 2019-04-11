---
id: first-unique-character-in-a-string
title: First Unique Character in a String
sidebar_label: First Unique Character in a String
---
## Description
<div class="description">
<p>
Given a string, find the first non-repeating character in it and return it's index. If it doesn't exist, return -1.
</p>
<p><b>Examples:</b>
<pre>
s = "leetcode"
return 0.

s = "loveleetcode",
return 2.
</pre>
</p>

<p>
<b>Note:</b> You may assume the string contain only lowercase letters.
</p>
</div>

## Solution
```javascript
/**
 * @param {string} s
 * @return {number}
 */
const firstUniqChar = (s) => {
  const map = Array.prototype.reduce.call(s, (acc, c) => {
    if (acc[c]) {
      acc[c]++
    } else {
      acc[c] = 1
    }
    return acc
  }, {})
  return Array.prototype.findIndex.call(s, c => map[c] === 1)
}
```
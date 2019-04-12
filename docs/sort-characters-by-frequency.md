---
id: sort-characters-by-frequency
title: Sort Characters By Frequency
sidebar_label: Sort Characters By Frequency
---
## Description
<div class="description">
<p>Given a string, sort it in decreasing order based on the frequency of characters.</p>

<p><b>Example 1:</b>
<pre>
<b>Input:</b>
"tree"

<b>Output:</b>
"eert"

<b>Explanation:</b>
'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.
</pre>
</p>

<p><b>Example 2:</b>
<pre>
<b>Input:</b>
"cccaaa"

<b>Output:</b>
"cccaaa"

<b>Explanation:</b>
Both 'c' and 'a' appear three times, so "aaaccc" is also a valid answer.
Note that "cacaca" is incorrect, as the same characters must be together.
</pre>
</p>

<p><b>Example 3:</b>
<pre>
<b>Input:</b>
"Aabb"

<b>Output:</b>
"bbAa"

<b>Explanation:</b>
"bbaA" is also a valid answer, but "Aabb" is incorrect.
Note that 'A' and 'a' are treated as two different characters.
</pre>
</p>
</div>

## Solution(javascript)
```javascript
const frequencySort = (s) => {
  const map = {}
  for (c of s) {
    if (map[c]) {
      map[c]++
    } else {
      map[c] = 1
    }
  }
  console.log(map)
  const toStr = (c, count) => {
    let current = c
    while (count > 1) {
      current += c
      count--
    }
    return current
  }
  return Object.keys(map)
    .sort((keyA, keyB) => map[keyB] - map[keyA])
    .map(key => toStr(key, map[key]))
    .join('')
}
```
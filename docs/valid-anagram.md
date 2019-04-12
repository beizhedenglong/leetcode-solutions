---
id: valid-anagram
title: Valid Anagram
sidebar_label: Valid Anagram
---
## Description
<div class="description">
<p>Given two strings <em>s</em> and <em>t&nbsp;</em>, write a function to determine if <em>t</em> is an anagram of <em>s</em>.</p>

<p><b>Example 1:</b></p>

<pre>
<b>Input:</b> <em>s</em> = &quot;anagram&quot;, <em>t</em> = &quot;nagaram&quot;
<b>Output:</b> true
</pre>

<p><b>Example 2:</b></p>

<pre>
<b>Input:</b> <em>s</em> = &quot;rat&quot;, <em>t</em> = &quot;car&quot;
<b>Output: </b>false
</pre>

<p><strong>Note:</strong><br />
You may assume the string contains only lowercase alphabets.</p>

<p><strong>Follow up:</strong><br />
What if the inputs contain unicode characters? How would you adapt your solution to such case?</p>

</div>

## Solution(javascript)
```javascript
const wordPattern = (pattern, str) => {
  const patternMap = Array.prototype.reduce.call(pattern, (map, c, index) => {
    if (map[c]) {
      map[c]++
    } else {
      map[c] = 1
    }
    return map
  }, {})
  const wordArr = str.split(' ')
  if (wordArr.length !== pattern.length) {
    return false
  }
  const wordMap = wordArr.reduce((map, word) => {
    if (map[word]) {
      map[word]++
    } else {
      map[word] = 1
    }
    return map
  }, {})
  for (let i = 0; i < pattern.length; i++) {
    if (patternMap[pattern[i]] !== wordMap[wordArr[i]]) {
      return false
    }
  }
  return true
}


const isAnagram = (s, t) => {
  const map = {}
  if (s.length !== t.length) {
    return false
  }
  for (c of s) {
    if (map[c]) {
      map[c]++
    } else {
      map[c] = 1
    }
  }
  for (c of t) {
    if (!map[c]) {
      return false
    }
    map[c]--
  }
  for (c of s) {
    if (map[c] !== 0) {
      return false
    }
  }
  return true
}

```
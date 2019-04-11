---
id: word-pattern
title: Word Pattern
sidebar_label: Word Pattern
---
## Description
<div class="description">
<p>Given a <code>pattern</code> and a string <code>str</code>, find if <code>str</code> follows the same pattern.</p>

<p>Here <b>follow</b> means a full match, such that there is a bijection between a letter in <code>pattern</code> and a <b>non-empty</b> word in <code>str</code>.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>Output:</strong> true</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong>pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog cat cat fish&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;aaaa&quot;</code>, str = <code>&quot;dog cat cat dog&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 4:</strong></p>

<pre>
<strong>Input:</strong> pattern = <code>&quot;abba&quot;</code>, str = <code>&quot;dog dog dog dog&quot;</code>
<strong>Output:</strong> false</pre>

<p><b>Notes:</b><br />
You may assume <code>pattern</code> contains only lowercase letters, and <code>str</code> contains lowercase letters that may be separated by a single space.</p>

</div>

## Solution
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

```
---
id: reverse-words-in-a-string-iii
title: Reverse Words in a String III
sidebar_label: Reverse Words in a String III
---
## Description
<div class="description">
<p>Given a string, you need to reverse the order of characters in each word within a sentence while still preserving whitespace and initial word order.</p>

<p><b>Example 1:</b><br />
<pre>
<b>Input:</b> "Let's take LeetCode contest"
<b>Output:</b> "s'teL ekat edoCteeL tsetnoc"
</pre>
</p>

<p><b>Note:</b>
In the string, each word is separated by single space and there will not be any extra space in the string.
</p>
</div>

## Solution(javascript)
```javascript
/**
 * @param {string} str
 * @returns {string}
 */
const reverseWords = str => str.trim()
  .split(/\s+/)
  .map((s) => {
    let returned = ''
    for (let i = s.length-1; i >= 0; i--) {
      returned += s[i]
    }
    return returned
  })
  .join(' ')

```
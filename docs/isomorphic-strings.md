---
id: isomorphic-strings
title: Isomorphic Strings
sidebar_label: Isomorphic Strings
---
## Description
<div class="description">
<p>Given two strings <b><i>s</i></b> and <b><i>t</i></b>, determine if they are isomorphic.</p>

<p>Two strings are isomorphic if the characters in <b><i>s</i></b> can be replaced to get <b><i>t</i></b>.</p>

<p>All occurrences of a character must be replaced with another character while preserving the order of characters. No two characters may map to the same character but a character may map to itself.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <b><i>s</i></b> = <code>&quot;egg&quot;, </code><b><i>t = </i></b><code>&quot;add&quot;</code>
<strong>Output:</strong> true
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <b><i>s</i></b> = <code>&quot;foo&quot;, </code><b><i>t = </i></b><code>&quot;bar&quot;</code>
<strong>Output:</strong> false</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> <b><i>s</i></b> = <code>&quot;paper&quot;, </code><b><i>t = </i></b><code>&quot;title&quot;</code>
<strong>Output:</strong> true</pre>

<p><b>Note:</b><br />
You may assume both <b><i>s&nbsp;</i></b>and <b><i>t&nbsp;</i></b>have the same length.</p>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string} s
 * @param {string} t
 * @return {boolean}
 */
const isIsomorphic = (s, t = '') => {
  const count = str => Array.prototype.reduce.call(str, (map, c, index) => {
    if (map[c]) {
      map[c].push(index)
    }
    map[c] = [index]
    return map
  }, {})
  const mapS = count(s)
  const mapT = count(t)

  for (let i = 0; i < s.length; i++) {
    const charS = s[i]
    const charT = t[i]
    for (let j = 0; j < mapS[charS].length; j++) {
      if (mapS[charS][j] !== mapT[charT][j]) {
        return false
      }
    }
  }
  return true
}

```
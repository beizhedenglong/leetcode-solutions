---
id: keyboard-row
title: Keyboard Row
sidebar_label: Keyboard Row
---
## Description
<div class="description">
<p>Given a List of words, return the words that can be typed using letters of <b>alphabet</b> on only one row&#39;s of American keyboard like the image below.</p>

<p>&nbsp;</p>

<p><img alt="" src="https://assets.leetcode.com/uploads/2018/10/12/keyboard.png" style="width: 100%; max-width: 600px" /></p>
&nbsp;

<p><b>Example:</b></p>

<pre>
<b>Input:</b> [&quot;Hello&quot;, &quot;Alaska&quot;, &quot;Dad&quot;, &quot;Peace&quot;]
<b>Output:</b> [&quot;Alaska&quot;, &quot;Dad&quot;]
</pre>

<p>&nbsp;</p>

<p><b>Note:</b></p>

<ol>
	<li>You may use one character in the keyboard more than once.</li>
	<li>You may assume the input string will only contain letters of alphabet.</li>
</ol>

</div>

## Solution(javascript)
```javascript
/**
 * @param {string[]} words
 * @return {string[]}
 */
const findWords = (words) => {
  const firstRow = 'qwertyuiop'
  const secondRow = 'asdfghjkl'
  const thirdRow = 'zxcvbnm'
  const dict = {}
  const generateDict = (d, row, num) => {
    for (c of row) {
      d[c] = num
    }
  }
  generateDict(dict, firstRow, 1)
  generateDict(dict, secondRow, 2)
  generateDict(dict, thirdRow, 3)
  const isSameRow = (word = '') => {
    word = word.toLowerCase()
    let previous = null
    for (c of word) {
      if (previous && dict[c] !== previous) {
        return false
      }
      previous = dict[c]
    }
    return previous
  }
  return words.filter(isSameRow)
}

```
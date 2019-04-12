---
id: generate-parentheses
title: Generate Parentheses
sidebar_label: Generate Parentheses
---
## Description
<div class="description">
<p>
Given <i>n</i> pairs of parentheses, write a function to generate all combinations of well-formed parentheses.
</p>

<p>
For example, given <i>n</i> = 3, a solution set is:
</p>
<pre>
[
  "((()))",
  "(()())",
  "(())()",
  "()(())",
  "()()()"
]
</pre>
</div>

## Solution(javascript)
```javascript
/**
 * @param {number} n
 * @return {string[]}
 */

const fill = (item, start, end) => {
  const res = []
  for (let i = start; i < end; i++) {
    res.push(item)
  }
  return res
}

const generateParenthesis = (n) => {
  const left = fill('(', 0, n)
  const right = fill(')', 0, n)
  const res = []
  const aux = (acc, accLeft, accRight) => {
    if (accLeft.length === 0) {
      acc = [...acc, ...accRight]
      res.push(acc)
    } else if (accLeft.length < accRight.length) {
      const [hd1, ...rest1] = accLeft
      const [hd2, ...rest2] = accRight
      const acc1 = [...acc, hd1]
      const acc2 = [...acc, hd2]
      aux(acc1, rest1, accRight)
      aux(acc2, accLeft, rest2)
    } else {
      const [hd1, ...rest1] = accLeft
      const acc1 = [...acc, hd1]
      aux(acc1, rest1, accRight)
    }
  }
  aux([], left, right)
  return res.map(x => x.join(''))
}




```
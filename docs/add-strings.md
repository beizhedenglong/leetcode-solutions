---
id: add-strings
title: Add Strings
sidebar_label: Add Strings
---
## Description
<div class="description">
<p>Given two non-negative integers <code>num1</code> and <code>num2</code> represented as string, return the sum of <code>num1</code> and <code>num2</code>.</p>

<p><b>Note:</b>
<ol>
<li>The length of both <code>num1</code> and <code>num2</code> is < 5100.</li>
<li>Both <code>num1</code> and <code>num2</code> contains only digits <code>0-9</code>.</li>
<li>Both <code>num1</code> and <code>num2</code> does not contain any leading zero.</li>
<li>You <b>must not use any built-in BigInteger library</b> or <b>convert the inputs to integer</b> directly.</li>
</ol>
</p>
</div>

## Solution
```javascript
/**
 * @param {string} num1
 * @param {string} num2
 * @return {string}
 */
var addStrings =  (num1, num2) => {
  const reversedNum1 = num1.split('').reverse()
  const reversedNum2 = num2.split('').reverse()
  const { shorter, longer } = reversedNum1.length < reversedNum2.length
    ? { shorter: reversedNum1, longer: reversedNum2 }
    : { shorter: reversedNum2, longer: reversedNum1 }

  let rem = 0
  let result = longer.reduce((acc, digit1, index) => {
    const total = parseInt(digit1, 10) + (parseInt(shorter[index], 10) || 0) + rem
    if (total >= 10) {
      rem = 1
    } else {
      rem = 0
    }
    return [
      ...acc,
      total >= 10 ? total - 10 : total,
    ]
  }, [])
  result = rem === 1 ? [...result, rem] : result
  return result.reverse().join('')
}

```
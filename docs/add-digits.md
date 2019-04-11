---
id: add-digits
title: Add Digits
sidebar_label: Add Digits
---
## Description
<div class="description">
<p>Given a non-negative integer <code>num</code>, repeatedly add all its digits until the result has only one digit.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> <code>38</code>
<strong>Output:</strong> 2 
<strong>Explanation: </strong>The process is like: <code>3 + 8 = 11</code>, <code>1 + 1 = 2</code>. 
&nbsp;            Since <code>2</code> has only one digit, return it.
</pre>

<p><b>Follow up:</b><br />
Could you do it without any loop/recursion in O(1) runtime?</p>
</div>

## Solution
```javascript
/**
 * @param {number} num
 * @return {number}
 */
var addDigits = function(num) {
    function cal(num){
        var s = num.toString();
        var digits = s.split("").map(Number);
        if(digits.length === 1){
            return digits[0];
        }
        num = digits.reduce(function(pre, cur){
            return pre + cur;
        });
        return cal(num);
    }
    
    return cal(num);
};
```
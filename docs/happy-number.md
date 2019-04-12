---
id: happy-number
title: Happy Number
sidebar_label: Happy Number
---
## Description
<div class="description">
<p>Write an algorithm to determine if a number is &quot;happy&quot;.</p>

<p>A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.</p>

<p><strong>Example:&nbsp;</strong></p>

<pre>
<strong>Input:</strong> 19
<strong>Output:</strong> true
<strong>Explanation: 
</strong>1<sup>2</sup> + 9<sup>2</sup> = 82
8<sup>2</sup> + 2<sup>2</sup> = 68
6<sup>2</sup> + 8<sup>2</sup> = 100
1<sup>2</sup> + 0<sup>2</sup> + 0<sup>2</sup> = 1
</pre>
</div>

## Solution(javascript)
```javascript
/**
 * @param {number} n
 * @return {boolean}
 */
var isHappy = function(n) {
    
    var arr = [];
    // helper function
    function cal(n){
        if(n === 1){
            return true;
        }
        arr.push(n);
        var s = n.toString();
        var digits = s.split("").map(Number),
            sum = 0;
        for(var i = 0; i < digits.length; i++){
              sum += digits[i]*digits[i];
        }
        if(arr.indexOf(sum) !== -1){
            return false;
        }
        return cal(sum);
    }
    
      return cal(n);
};
```
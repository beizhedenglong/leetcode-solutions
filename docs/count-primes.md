---
id: count-primes
title: Count Primes
sidebar_label: Count Primes
---
## Description
<div class="description">
<p>Count the number of prime numbers less than a non-negative number, <b><i>n</i></b>.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong> 10
<strong>Output:</strong> 4
<strong>Explanation:</strong> There are 4 prime numbers less than 10, they are 2, 3, 5, 7.
</pre>

</div>

## Solution
```javascript
/**
 * @param {number} n
 * @return {number}
 */

const countPrimes = (n) => {
  const map = []
  for (let i = 2; i < n; i++) {
    map[i] = true
  }
  for (let i = 2; i * i < n; i++) {
    if (map[i]) {
      for (let j = i * i; j < n; j += i) {
        map[j] = false
      }
    }
  }
  return map.filter(num => num === true).length
}


```
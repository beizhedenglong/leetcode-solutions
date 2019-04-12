---
id: sqrtx
title: Sqrt(x)
sidebar_label: Sqrt(x)
---
## Description
<div class="description">
<p>Implement <code>int sqrt(int x)</code>.</p>

<p>Compute and return the square root of <em>x</em>, where&nbsp;<em>x</em>&nbsp;is guaranteed to be a non-negative integer.</p>

<p>Since the return type&nbsp;is an integer, the decimal digits are truncated and only the integer part of the result&nbsp;is returned.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 4
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 8
<strong>Output:</strong> 2
<strong>Explanation:</strong> The square root of 8 is 2.82842..., and since 
&nbsp;            the decimal part is truncated, 2 is returned.
</pre>

</div>

## Solution(javascript)
```javascript
/**
 * @param {number} x
 * @return {number}
 */
// const mySqrt = (x) => {
//   const aux = (low, high) => {
//     if (low > high) {
//       return null
//     }
//     const middle = Math.floor((low + high) / 2)
//     const left = middle - 1
//     const right = middle + 1
//     if ((middle * middle <= x) && (right * right > x)) {
//       return middle
//     }
//     if (middle * middle < x) {
//       return aux(right, high)
//     }
//     return aux(low, left)
//   }
//   return aux(0, x)
// }


const mySqrt = (x) => {
  let r = x
  while (r * r > x) {
    r = Math.floor((r + x / r) / 2)
  }

  return r
}
```
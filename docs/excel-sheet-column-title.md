---
id: excel-sheet-column-title
title: Excel Sheet Column Title
sidebar_label: Excel Sheet Column Title
---
## Description
<div class="description">
<p>Given a positive integer, return its corresponding column title as appear in an Excel sheet.</p>

<p>For example:</p>

<pre>
    1 -&gt; A
    2 -&gt; B
    3 -&gt; C
    ...
    26 -&gt; Z
    27 -&gt; AA
    28 -&gt; AB 
    ...
</pre>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 1
<strong>Output:</strong> &quot;A&quot;
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 28
<strong>Output:</strong> &quot;AB&quot;
</pre>

<p><strong>Example 3:</strong></p>

<pre>
<strong>Input:</strong> 701
<strong>Output:</strong> &quot;ZY&quot;
</pre>
</div>

## Solution
```javascript
/**
 * @param {number} n
 * @return {string}
 */
var convertToTitle = function(n) {
    var A = "A".charCodeAt(0);
    var str = "";
    while(n > 0) {
        n--;
        str = String.fromCharCode(A+n%26) + str;
        n =parseInt(n/26);
    }
    
    return str;
};
```
---
id: insert-delete-getrandom-o1
title: Insert Delete GetRandom O(1)
sidebar_label: Insert Delete GetRandom O(1)
---
## Description
<div class="description">
<p>Design a data structure that supports all following operations in <i>average</i> <b>O(1)</b> time.</p>

<p>
<ol>
<li><code>insert(val)</code>: Inserts an item val to the set if not already present.</li>
<li><code>remove(val)</code>: Removes an item val from the set if present.</li>
<li><code>getRandom</code>: Returns a random element from current set of elements. Each element must have the <b>same probability</b> of being returned.</li>
</ol>
</p>

<p><b>Example:</b>
<pre>
// Init an empty set.
RandomizedSet randomSet = new RandomizedSet();

// Inserts 1 to the set. Returns true as 1 was inserted successfully.
randomSet.insert(1);

// Returns false as 2 does not exist in the set.
randomSet.remove(2);

// Inserts 2 to the set, returns true. Set now contains [1,2].
randomSet.insert(2);

// getRandom should return either 1 or 2 randomly.
randomSet.getRandom();

// Removes 1 from the set, returns true. Set now contains [2].
randomSet.remove(1);

// 2 was already in the set, so return false.
randomSet.insert(2);

// Since 2 is the only number in the set, getRandom always return 2.
randomSet.getRandom();
</pre>
</p>
</div>

## Solution
```javascript
/**
 * Initialize your data structure here.
 */
const swap = (arr, indexA, indexB) => {
  const temp = arr[indexA]
  arr[indexA] = arr[indexB]
  arr[indexB] = temp
}
const RandomizedSet = function () {
  this.map = {}
  this.arr = []
}

/**
 * Inserts a value to the set. Returns true if the set did not already contain the specified element.
 * @param {number} val
 * @return {boolean}
 */
RandomizedSet.prototype.insert = function (val) {
  const index = this.map[val]
  if (index !== undefined) {
    return false
  }
  this.arr.push(val)
  this.map[val] = this.arr.length - 1
  return true
}

/**
 * Removes a value from the set. Returns true if the set contained the specified element.
 * @param {number} val
 * @return {boolean}
 */
RandomizedSet.prototype.remove = function (val) {
  const index = this.map[val]
  if (index !== undefined) {
    if (index !== (this.arr.length - 1)) {
      this.map[this.arr[this.arr.length - 1]] = index
      swap(this.arr, index, this.arr.length - 1)
    }
    delete this.map[val]
    this.arr.pop()
    return true
  }
  return false
}

/**
 * Get a random element from the set.
 * @return {number}
 */
RandomizedSet.prototype.getRandom = function () {
  const randomIndex = Math.floor(Math.random() * this.arr.length)
  return this.arr[randomIndex]
}

/**
 * Your RandomizedSet object will be instantiated and called as such:
 * var obj = Object.create(RandomizedSet).createNew()
 * var param_1 = obj.insert(val)
 * var param_2 = obj.remove(val)
 * var param_3 = obj.getRandom()
 */

```
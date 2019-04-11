---
id: kth-largest-element-in-an-array
title: Kth Largest Element in an Array
sidebar_label: Kth Largest Element in an Array
---
## Description
<div class="description">
<p>Find the <strong>k</strong>th largest element in an unsorted array. Note that it is the kth largest element in the sorted order, not the kth distinct element.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> <code>[3,2,1,5,6,4] </code>and k = 2
<strong>Output:</strong> 5
</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> <code>[3,2,3,1,2,4,5,5,6] </code>and k = 4
<strong>Output:</strong> 4</pre>

<p><strong>Note: </strong><br />
You may assume k is always valid, 1 &le; k &le; array&#39;s length.</p>

</div>

## Solution
```javascript
/**
 * @param {number[]} nums
 * @param {number} k
 * @return {number}
 */


const findKthLargest = (nums, k) => {
  const swap = (a, b, arr) => { // eslint-disable-line
    if (a !== b) {
      const temp = arr[a]
      arr[a] = arr[b] // eslint-disable-line
      arr[b] = temp // eslint-disable-line
    }
  }
  const Heap = compareFn => (arr = []) => {
    const left = index => 2 * index + 1
    const right = index => 2 * index + 2
    const parent = index => Math.floor((index - 1) / 2)
    const size = () => arr.length

    // log(n)
    const heapify = (index) => {
      const l = left(index)
      const r = right(index)
      let current = index
      if (compareFn(arr[current], arr[l]) > 0 && (l < size())) {
        current = l
      }
      if (compareFn(arr[current], arr[r]) > 0 && (r < size())) {
        current = r
      }
      if (current !== index) {
        swap(current, index, arr)
        heapify(current)
      }
    }
    // log(n)
    const heapifyUp = (index) => {
      const p = parent(index)
      if (p >= 0 && compareFn(arr[p], arr[index]) > 0) {
        swap(p, index, arr)
        heapifyUp(p)
      }
    }
    // O(n)
    const buildHeap = () => {
      for (let i = Math.floor(arr.length / 2); i >= 0; i--) {
        heapify(i)
      }
    }
    const extract = () => {
      swap(0, arr.length - 1, arr)
      const top = arr.pop()
      heapify(0)
      return top
    }
    buildHeap()
    return {
      extract,
      size: () => arr.length,
    }
  }
  const maxHeap = Heap((a, b) => b - a)(nums)

  while (k > 1 && maxHeap.size() > 1) {
    maxHeap.extract()
    k--
  }
  return maxHeap.extract()
}

```
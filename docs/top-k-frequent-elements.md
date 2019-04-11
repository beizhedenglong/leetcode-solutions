---
id: top-k-frequent-elements
title: Top K Frequent Elements
sidebar_label: Top K Frequent Elements
---
## Description
<div class="description">
<p>Given a non-empty array of integers, return the <b><i>k</i></b> most frequent elements.</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input: </strong>nums = <span id="example-input-1-1">[1,1,1,2,2,3]</span>, k = <span id="example-input-1-2">2</span>
<strong>Output: </strong><span id="example-output-1">[1,2]</span>
</pre>

<div>
<p><strong>Example 2:</strong></p>

<pre>
<strong>Input: </strong>nums = <span id="example-input-2-1">[1]</span>, k = <span id="example-input-2-2">1</span>
<strong>Output: </strong><span id="example-output-2">[1]</span></pre>
</div>

<p><b>Note: </b></p>

<ul>
	<li>You may assume <i>k</i> is always valid, 1 &le; <i>k</i> &le; number of unique elements.</li>
	<li>Your algorithm&#39;s time complexity <b>must be</b> better than O(<i>n</i> log <i>n</i>), where <i>n</i> is the array&#39;s size.</li>
</ul>

</div>

## Solution
```javascript
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
  const remove = (item) => {
    const index = arr.findIndex(x => compareFn(x, item) === 0)
    if (index === -1) {
      return
    }
    arr[index] = arr.pop() // eslint-disable-line
    const p = parent(index)
    if (p < 0 || compareFn(p, arr[index]) < 0) {
      heapify(index)
    } else {
      heapifyUp(index)
    }
  }
  buildHeap()
  return {
    getHeap: () => arr,
    peek: () => {
      if (arr.length === 0) {
        return null
      }
      return arr[0]
    },
    add: (item) => {
      arr.push(item)
      heapifyUp(arr.length - 1)
    },
    extract,
    remove,
    size,
  }
}


const topKFrequent = function (nums = [], k) {
  const map = nums.reduce((acc, num) => {
    if (acc[num]) {
      acc[num] += 1
    } else {
      acc[num] = 1
    }
    return acc
  }, {})
  const maxHeap = Heap((a, b) => map[b] - map[a])(
    Object.keys(map).map(x => parseInt(x)),
  )
  const res = []
  for (let i = 1; i <= k; i++) {
    res.push(maxHeap.extract())
  }
  return res
}

```
---
id: merge-k-sorted-lists
title: Merge k Sorted Lists
sidebar_label: Merge k Sorted Lists
---
## Description
<div class="description">
<p>Merge <em>k</em> sorted linked lists and return it as one sorted list. Analyze and describe its complexity.</p>

<p><strong>Example:</strong></p>

<pre>
<strong>Input:</strong>
[
&nbsp; 1-&gt;4-&gt;5,
&nbsp; 1-&gt;3-&gt;4,
&nbsp; 2-&gt;6
]
<strong>Output:</strong> 1-&gt;1-&gt;2-&gt;3-&gt;4-&gt;4-&gt;5-&gt;6
</pre>

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
    if ((l < size()) && compareFn(arr[current], arr[l]) > 0) {
      current = l
    }
    if ((r < size()) && compareFn(arr[current], arr[r]) > 0) {
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

const mergeKLists = (lists = []) => {
  const minHeap = Heap((a, b) => a.val - b.val)([])
  lists.forEach((node) => {
    if (node) {
      minHeap.add(node)
    }
  })
  const head = minHeap.extract() || null
  let current = head
  while (minHeap.size() > 0) {
    if (current.next) {
      minHeap.add(current.next)
    }
    current.next = minHeap.extract()
    current = current.next
  }
  return head
}
```
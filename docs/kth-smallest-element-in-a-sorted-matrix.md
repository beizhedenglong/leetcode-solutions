---
id: kth-smallest-element-in-a-sorted-matrix
title: Kth Smallest Element in a Sorted Matrix
sidebar_label: Kth Smallest Element in a Sorted Matrix
---
## Description
<div class="description">
<p>Given a <i>n</i> x <i>n</i> matrix where each of the rows and columns are sorted in ascending order, find the kth smallest element in the matrix.</p>

<p>
Note that it is the kth smallest element in the sorted order, not the kth distinct element.
</p>

<p><b>Example:</b>
<pre>
matrix = [
   [ 1,  5,  9],
   [10, 11, 13],
   [12, 13, 15]
],
k = 8,

return 13.
</pre>
</p>

<p><b>Note: </b><br>
You may assume k is always valid, 1 &le; k &le; n<sup>2</sup>.</p>
</div>

## Solution(javascript)
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

/**
 * @param {number[][]} matrix
 * @param {number} k
 * @return {number}
 */
const kthSmallest = function (matrix = [], k) {
  const minHeap = Heap((a, b) => a.val - b.val)(
    matrix.map((arr, rowIndex) => ({
      val: arr[0],
      rowIndex,
      columnIndex: 0,
    })),
  )
  for (let i = 1; i < k; i++) {
    const { rowIndex, columnIndex } = minHeap.extract()
    if (matrix[rowIndex][columnIndex + 1] !== undefined) {
      minHeap.add({
        val: matrix[rowIndex][columnIndex + 1],
        rowIndex,
        columnIndex: columnIndex + 1,
      })
    }
  }
  return minHeap.extract().val
}

```
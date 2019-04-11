---
id: course-schedule
title: Course Schedule
sidebar_label: Course Schedule
---
## Description
<div class="description">
<p>There are a total of <i>n</i> courses you have to take, labeled from <code>0</code> to <code>n-1</code>.</p>

<p>Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: <code>[0,1]</code></p>

<p>Given the total number of courses and a list of prerequisite <b>pairs</b>, is it possible for you to finish all courses?</p>

<p><strong>Example 1:</strong></p>

<pre>
<strong>Input:</strong> 2, [[1,0]] 
<strong>Output: </strong>true
<strong>Explanation:</strong>&nbsp;There are a total of 2 courses to take. 
&nbsp;            To take course 1 you should have finished course 0. So it is possible.</pre>

<p><strong>Example 2:</strong></p>

<pre>
<strong>Input:</strong> 2, [[1,0],[0,1]]
<strong>Output: </strong>false
<strong>Explanation:</strong>&nbsp;There are a total of 2 courses to take. 
&nbsp;            To take course 1 you should have finished course 0, and to take course 0 you should
&nbsp;            also have finished course 1. So it is impossible.
</pre>

<p><b>Note:</b></p>

<ol>
	<li>The input prerequisites is a graph represented by <b>a list of edges</b>, not adjacency matrices. Read more about <a href="https://www.khanacademy.org/computing/computer-science/algorithms/graph-representation/a/representing-graphs" target="_blank">how a graph is represented</a>.</li>
	<li>You may assume that there are no duplicate edges in the input prerequisites.</li>
</ol>

</div>

## Solution
```javascript

const hasCycle = (arr) => {
  let cycle = false
  const visited = {}
  const aux = (node, adj = [], map) => {
    if (visited[node]) {
      return
    }
    if (map[node]) {
      cycle = true
    } else {
      map[node] = true
      adj.forEach(decentNode => aux(decentNode, arr[decentNode], { ...map }))
    }
    visited[node] = true
  }
  arr.forEach((adj, node) => {
    aux(node, adj, {})
  })
  return cycle
}

const canFinish = (numCourses, prerequisites) => {
  const dependence = prerequisites.reduce((acc, [course1, course2]) => {
    if (acc[course1]) {
      acc[course1].push(course2)
    } else {
      acc[course1] = [course2]
    }
    return acc
  }, [])
  return !hasCycle(dependence)
}

canFinish(0, [[0, 1], [0, 2], [0, 3]])

```
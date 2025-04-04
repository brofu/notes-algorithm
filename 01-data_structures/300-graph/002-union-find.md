## Union-Find. Problems of Connectivity in Un-Directed Graph

### Concepts 

* Connected Graph

    * The entire graph has only one connected component
    * There is a path between every pair of nodes

* Disconnected Graph

    * The graph is split into multiple parts
    * Each part is connected internally, but there are no edges between parts

* Connected Component
    
    * In an undirected graph, a connected component is a maximal subset of vertices such that there is a path between any two vertices within that subset

### Properties

* **Reflexivity**: A node p is connected to itself.

* **Symmetry**: If node p is connected to node q, then node q is also connected to node p.

* **Transitivity**: If node p is connected to node q, and node q is connected to node r, then node p is also connected to node r.

### Presentation

#### Logic Level 

`Forest`. Multiple trees (or Un-Directed Graph)

#### Code Level

[A basic Union Find implementation](https://github.com/brofu/leetcode/blob/main/graph/union_find/uf.go#L16), which is presenting multiple `Connected Component` with array.

### Problems 
| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [207. Course Schedule](https://leetcode.com/problems/course-schedule/description/) | 1. DFS<br> 2. BFS | 1. DFS. The order of `checking onPath` and `visited`<br> 2. The key idea of BFS. Refer to the code | [code](https://github.com/brofu/leetcode/blob/main/graph/graph_lc207.go) | | 
| - |- |- | - | - |




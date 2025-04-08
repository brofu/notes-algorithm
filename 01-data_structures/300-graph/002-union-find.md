## Union-Find. Problems of Connectivity in Un-Directed Graph

### Summary

> 并查集（Union Find）结构是二叉树结构的衍生，用于高效解决无向图的连通性问题，可以在
>
>O(1)时间内合并两个连通分量，
>
>O(1)时间内查询两个节点是否连通，
>
>O(1)时间内查询连通分量的数量。


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


### Optimizations

1. Record the `Weight` of each node, and balance the sub nodes of each node. O(lgN)
2. Compact the `Path` (from one node to it's root), since we only care about the root of the tree. O(1)

### Problems 
| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [323. Number of Connected Components in an Undirected Graph](https://leetcode.com/problems/number-of-connected-components-in-an-undirected-graph/description/) | | | [code](https://github.com/brofu/leetcode/blob/main/graph/union_find/uf_lc323.go) | | 
| [130. Surrounded Regions](https://leetcode.com/problems/surrounded-regions/description/) | 1. DFS<br> 2. Union-Find |2. 主要思路是适时增加虚拟节点，想办法让元素分门别类，建立动态连通关系。 | [code](https://github.com/brofu/leetcode/blob/main/graph/union_find/uf_lc130.go) | | 
| [990. Satisfiability of Equality Equations](https://leetcode.com/problems/satisfiability-of-equality-equations/description/) | Union-Find |根据 == 和 != 分成两部分，先处理 == 算式，使得他们连通；然后处理 != 算式，检查不等关系是否破坏相等关系的连通性。| [code](https://github.com/brofu/leetcode/blob/main/graph/union_find/uf_lc990.go) | | 
| [684. Redundant Connection](https://leetcode.com/problems/redundant-connection/description/) | Union-Find || [code](https://github.com/brofu/leetcode/blob/main/graph/union_find/uf_lc684.go) | | 
| [547. Number of Provinces](https://leetcode.com/problems/number-of-provinces/description/) | 1. BFS/DFS<br> 2. Union-Find || [code](https://github.com/brofu/leetcode/blob/main/graph/union_find/uf_lc547.go) | | 
| - |- |- | - | - |

### Problems - Validating Tree by Graph
| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [261. Graph Valid Tree](https://leetcode.com/problems/graph-valid-tree/description/) | | Refer to the code | [code](https://github.com/brofu/leetcode/blob/main/graph/union_find/uf_lc261.go) | | 
| - |- |- | - | - |

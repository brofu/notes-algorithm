# Graph

## Nature of `Graph`

`Graph` actually a `K-ary Tree`, which allows nodes pointing to it's `parent` node or `other` nodes (siblings, children, etc).

## Logic Level Presentation 
And it's logic presentation  can be like this, 

```
type Vertex struct {
    id        int
    neighbors []*Vertex  //
} 
```

It's very similar to the `K-ary Tree`

```
type TreeNode struct {
    val      int
    children []*TreeNode
}
```

## Code Level Presentation

* **`Adjacency List`**

   ```
    // graph[x] all the neighbors to x
    var graph [][]int
   ```

* **`Adjacency Matrix`**
    ```
    // matrix[x][y] if there E(x, y) exists
    var matrix [][]bool
    ```


* **`Adjacency List`** V.S.  **`Adjacency Matrix`** 

|Presentation| Complexity | Usage Scenarios |
|-|-|-|
|Adjacency List| 1. Space Complexity: O(V+E)<br>2. Check if E(u, v) exists: O(degree(u))<br>3. Iterate all neighbors of u: O(degree(u))|1. **Sparse Graph** (E « V^2)<br>2. High frequent iterating all the neighbors, such as DFS, BFS, Dijkstra etc.|
|Adjacency Matrix| 1. Space Complexity: O(V^2)<br>2. Check if E(u, v) exists: O(1)<br>3. Iterate all neighbors of u: O(V)|1. **Dense Graph** <br>2. High frequent to check if E(u, v) exists, for example, `Floyd-Warshall`|


## Concepts

* `Degree`. `InDegree`, `OutDegree`

## Sub Types 

Above mentioned topics are based on `Directed Unweighted Graph`. But there are more sub types of Graph. 

* **Directed Weighted Graph**

```
// Adjacency List     

type Edge struct {
    To int
    Weight int
}
// graph[x], all the neighbors of x, with weight
var graph [][]Edge


// Adjacency Matrix

// graph[u][v], the weight of E(u,v). if 0, means E(u, v) not exists
var graph [][]int
```

* **Undirected Weighted/Unweighted Graph**

`Undirected` actually means `each-direction` between 2 nodes. So, I can be presented by above code

## Common Algorithms of Sub Types

|Sub Type| Algorithms | Comments |
|-|-|-|
| Undirected Graph | ||
| Directed Weighted Graph | ||
| Directed Unweighted Graph | ||


## Code Template

Take `Directed Weighted Graph` as an example. Since all the other can be presented by this also

[An implementation of `Directed Weighted Grap` based on `Adjacency List`](https://github.com/brofu/leetcode/blob/main/graph/graph.go)



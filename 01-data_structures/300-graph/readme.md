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


## DFS

### Traverse Vertices(nodes) of Graph 

* Key difference between `traverse nodes of a graph` and `traver nodes of a tree`

>图的遍历就是多叉树遍历 的延伸，主要遍历方式还是深度优先搜索（DFS）和广度优先搜索（BFS）。
>
>唯一的区别是，树结构中不存在环，而图结构中可能存在环，所以我们需要标记遍历过的节点，避免遍历函数在环中死循环。
>
>遍历图的「节点」和「路径」略有不同，遍历「节点」时，需要 visited 数组在前序位置标记节点；遍历图的所有「路径」时，需要 onPath 数组在前序位置标记节点，在后序位置撤销标记。


* Code Difference

```
type Node struct {
    val      int
    children []*Node
}

func traverse(root *Node) {
    if root == nil {
        return
    }
    fmt.Println("visit", root.val) // pre-order location
    for _, child := range root.children {
        traverse(child)
    }
    // post-order location
}

type Vertex struct {
    id        int
    neighbors []*Vertex
}
func traverse(s *Vertex, visited []bool) {
    if s == nil {
        return
    }
    if visited[s.id] { // the usage of `vistied`
        return
    }

    visited[s.id] = true // pre-order location
    fmt.Println("visit", s.id)
    for _, neighbor := range s.neighbors {
        traverse(neighbor, visited)
    }
    // post-order location
}
```

* Time Complexity

   * `Graph` O(V+E).   
   * `Binary Tree` O(N) 
   * Why time complexity of `Banary Tree` is O(N), instead of some thing like O(N + E)? 


### Traverse Edges(paths) of Graph 

* Key difference between `traverse paths of a graph` and `traver paths of a tree`

> 对于树结构，遍历所有「路径」和遍历所有「节点」是没什么区别的。而对于图结构，遍历所有「路径」和遍历所有「节点」稍有不同。
>
>因为对于树结构来说，只能由父节点指向子节点，所以从根节点 root 出发，到任意一个节点 targetNode 的路径都是唯一的。换句话说，我遍历一遍树结构的所有节点之后，必然可以找到 root 到 targetNode 的唯一路径：


```
// K-ary Tree

var path []*Node

func traverse(root *Node, targetNode *Node) {

	// base case
	if root == nil {
		return
	}

    // pre-order location
	path = append(path, root)
	if root.val == targetNode.val { // found the target
		for _, node := range path {
			fmt.Printf("%d ", node.val)
		}
        return
	}

	for _, child := range root.children {
		traverse(child, targetNode)
	}

	// post-order location
	path = path[:len(path)-1]
}


// Graph. Find all the paths to target node

var onPath []bool = make([]bool, graph.size())
var path []int

func traverse(graph Graph, src int, dest int) {

    // base case
    if src < 0 || src >= graph.size() {
        return
    }

    if onPath[src] {
        return
    }

    // pre-order location
    onPath[src] = true
    path = append(path, src)
    if src == dest { // find the target
        fmt.Println("find path:", path)
        return
    }

    for _, e := range graph.neighbors(src) {
        traverse(graph, e.to, dest)
    }

    // post-order location
    path = path[:len(path)-1]

    onPath[src] = false //why this?
}

```

>为什么遍历节点就不用撤销 visited 数组的标记，而遍历路径需要在后序位置撤销 onPath 数组的标记呢？
>
>因为遍历节点，visited 数组的职责是保证每个节点只会被访问一次。而对于图结构来说，要想遍历所有路径，可能会多次访问同一个节点，这是关键的区别。


###  About `visited` and `onPath`

## BFS

>图结构的广度优先搜索其实就是多叉树的层序遍历，无非就是加了一个 visited 数组来避免重复遍历节点。
>
理论上BFS遍历也需要区分遍历所有「节点」和遍历所有「路径」，但是实际上 BFS 算法一般只用来寻找那条最短路径，不会用来求所有路径。

Three code templates of BFS on a `Graph`

    * Without Steps/Depths
    * With Steps/Depths
    * With Weights



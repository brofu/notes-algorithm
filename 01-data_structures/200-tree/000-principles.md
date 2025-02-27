## Natures

**Presentation At Code Level**

```uml
@startmindmap

* Presentation 

**:<b>linked node</b>
For most tree related problems;
***:<b>example</b>
<code>
type Node struct {
    val      int
    Left  *TreeNode
    Right *TreeNode
}
</code>
;
**:<b>array</b>
1. binary heap
2. Union-Find;
***:<b>example</b>
<code>
</code>
;

**:<b>hashtab</b>
grap relevant problems;
***:<b>example</b>
<code>
// also know as Adjacency List
tree := map[int][]int{
    1: {2, 3},
    2: {4},
    3: {5, 6},
}
</code>
;

@endmindmap
```

**Traverse**

1. BF
    * Usually based on `Queue`
    * Can also use recursive
2. DF
    * PreOrder
    * InOrder
    * PostOrder

**Natural Connection**

* The nature of `Binary Tree`, `N-ary Tree` and `Forest` are actually `SAME`. The only differences are ONLY

    * How many children are there in the tree
    * In `Forest`, there are multiple tress
    * The presentation of `Tree` and `Forest` are different

* Binary Tree -> N-ary Tree -> Forest

```uml

@startmindmap

* Tree 

**: Binary Tree
<code>
type Node struct {
    val      int
    Left  *TreeNode
    Right *TreeNode
}
</code>;

*** DFS
****: <b>Code</b> 
<code>
func Traverse(root *TreeNode) {
    if root == nil {
        return
    }
    // pre-order location. do something...
    traverse(root.Left)
    // in-order location.do something...
    traverse(root.Right)
    // post-order location. do something...
}
</code>;

*** BFS
****: <b>Code - Scenairo 1</b> 
<code>
func Travese(root *TreeNode) {
    if root == nil {
        return
    }
    q := []*TreeNode{root}
    depth := 1

    for len(q) > 0 {
        sz := len(q)
        for i := 0; i < sz; i++ {
            cur := q[i]
            // do something with current node
            fmt.Printf("depth = %d, val = %d\n", depth, cur.Val)

            // handle children
            if cur.Left != nil {
                q = append(q, cur.Left)
            }
            if cur.Right != nil {
                q = append(q, cur.Right)
            }
        }
        q = q[size:]
        depth++
    }
}
</code>;

*****: <b>Code - Senario 2</b> 
type State struct {
    node  *TreeNode
    depth int
}

func Traverse(root *TreeNode) {
    if root == nil {
        return
    }
    q := []State{{root, 1}}

    for len(q) > 0 {
        size := len(q)
        for i:=0; i<size; i++ {
            cur := q[i]
            // do something with current node
            fmt.Printf("depth = %d, val = %d\n", cur.depth, cur.node.Val)

            // handle children
            if cur.node.Left != nil {
                q = append(q, State{cur.node.Left, cur.depth + 1})
            }
            if cur.node.Right != nil {
                q = append(q, State{cur.node.Right, cur.depth + 1})
            }
        }
        q = q[size:]
    }
}
</code>;

**: <b>NaryTree</b>
<code>
type Node struct {
    val      int
    children []*Node
}
</code>;

*** DFS
****: Code 
<code>
func TraverseNary(root *Node) {
    if root == nil {
        return
    }
    // pre-order location. do something...
    for _, child := range root.Children {
        traverseNary(child)
    }
    // post-order location. do something...
}
</code>;

*** BFS
****: <b>Code - Scenario 1</b>
<code>
func TraverseNary(root *Node) {
    if root == nil {
        return
    }
    q := []*Node{root}
    depth := 1
    for len(q) > 0 {
        sz := len(q)
        for i := 0; i < sz; i++ {
            cur := q[i]
            // do something with the node
            // handle children
            for _, child := range cur.children {
                q = append(q, child)
            }
        }
        q = q[size:]
        depth++
    }
}
</code>;

*****: <b>Code - Senario 2</b>
<code>
type State struct {
    node  *Node
    depth int
}

func TraveseNary(root *Node) {
    if root == nil {
        return
    }
    q := []State{}
    q = append(q, State{root, 1})

    for len(q) > 0 {
        sz := len(q)
        for i := 0; i < sz; i++ {
            state := q[i]
            cur := state.node
            depth := state.depth
            // do soemthing with current node
            fmt.Printf("depth = %d, val = %d\n", depth, cur.Val)
            // handle children
            for _, child := range cur.Children {
                q = append(q, State{child, depth + 1}) // record the depth of each node
            }
        }
        q = q[size:]
    }
}
</code>;


** Forest
@endmindmap
```

## Thinking Patterns

**PreOrder V.S. PostOrder**

Think about the `Quick Sort` and `Merge Sort` from the view of `Binary Tree`:

```uml
@startmindmap

* Pre Or Post ? 

**:PreOrder 
Only have info of 
current node 
parents node
But NO childre nodes;

***:Example - QuickSort
<code>
func sort(nums []int, lo int, hi int) {
    // pre-order location
    p := partition(nums, lo, hi)
    // childrens
    sort(nums, lo, p - 1)
    sort(nums, p + 1, hi)
}
</code>;

**:PostOrder
Has all the info of
current node, 
parent nodes,
children nodes;

***:Example - MergeSort
<code>
func sort(nums []int, lo int, hi int) {
    mid := (lo + hi) / 2
    // childrens first
    sort(nums, lo, mid)
    sort(nums, mid + 1, hi)
    // post-order location
    merge(nums, lo, mid, hi)
}
</code>;

@endmindmap
```

>前中后序是遍历二叉树过程中处理每一个节点的三个特殊时间点
>
>二叉树的所有问题，就是在前中后序位置注入巧妙的代码逻辑，去达到目的. 
>
>仔细观察，前中后序位置的代码，能力依次增强。
>
前序位置的代码只能从函数参数中获取父节点传递来的数据。
>
中序位置的代码不仅可以获取参数数据，还可以获取到左子树通过函数返回值传递回来的数据。
>
后序位置的代码最强，不仅可以获取参数数据，还可以同时获取到左右子树通过函数返回值传递回来的数据。
>
所以，某些情况下把代码移到后序位置效率最高；有些事情，只有后序位置的代码能做。


**Tree Traverse V.S. Sub Tasks**

Two ways to resolve Binary Tree relevant problems:

* Tree Traverse. `Traverse` 
* Recursive with sub trees. `Sub Tasks`

> 二叉树解题的思维模式分两类：
>
1、是否可以通过遍历一遍二叉树得到答案？如果可以，用一个 traverse 函数配合外部变量来实现，这叫「遍历」的思维模式。
>
2、是否可以定义一个递归函数，通过子问题（子树）的答案推导出原问题的答案？如果可以，写出这个递归函数的定义，并充分利用这个函数的返回值，这叫「分解问题」的思维模式。
>
无论使用哪种思维模式，都需要思考：
>
如果单独抽出一个二叉树节点，它需要做什么事情？需要在什么时候（前/中/后序位置）做？其他的节点不用操心，递归函数会帮你在所有节点上执行相同的操作。
>
>这两类思路分别对应着 回溯算法核心框架(and DFS) 和 动态规划核心框架。


Similarity to `Backtrack`, `DFS` and `Dynamic Programming`, `Divide and conquer`

>动归/DFS/回溯算法都可以看做二叉树问题的扩展，只是它们的关注点不同：
>
动态规划算法属于分解问题（分治）的思路，它的关注点在整棵「子树」。它的着眼点永远是结构相同的整个子问题，类比到二叉树上就是「子树」。
>
>回溯算法属于遍历的思路，它的关注点在节点间的「树枝」,即需要关注路径。它的着眼点永远是在节点之间移动的过程，类比到二叉树上就是「树枝」。
>
DFS 算法属于遍历的思路，它的关注点在单个「节点」。 它的着眼点永远是在单一的节点上，类比到二叉树上就是处理每个「节点」。

Compare the core code framework of problems of `Backtrack`, `DFS` and `Dynamic Programming`:

```uml
@startmindmap

* Traverse Or Sub Task?

**:Traverse 
Natrually similar as Backtrack or DFS;

***:Backtrack
<code>
// backtrack code framework
func backtrack([]int nums) { 
    for i := 0; i < len(nums); i++) {
        // choose
        used[i] = true
        track.addLast(nums[i])
        // entry next layer
        backtrack(nums)
        // cancel choose
        track.removeLast()
        used[i] = false
    }
}
</code>;

***:DFS
<code>
// Island Problem
func dfs([][]int grid, i, j int) { // DFS coding framework
    m := len(grid)
    n = len(grid[0])
    if (i < 0 || j < 0 || i >= m || j >= n) {
        return
    }
    if (grid[i][j] == 0) {
        return
    }
    // handle current node
    grid[i][j] = 0
    // entry next layer
    dfs(grid, i + 1, j)
    dfs(grid, i, j + 1)
    dfs(grid, i - 1, j)
    dfs(grid, i, j - 1)
}
</code>;

**:Sub Task
Natrually similar as Dynamic Programming;

***:Dynaimic Programming
<code>
// return the number of total nodes
func fib(N int) int {
    if N == 1 || N == 2 {
        return 1
    }
    // resolve the problem by resolving the sub-trees
    left := fib(N-1)
    right := fib(N - 2)
    // post-order location
    return left + right
}
</code>;

***:Divide and conquer
<code>
</code>;

@endmindmap
```


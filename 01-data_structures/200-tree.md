# Tree

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

**Principles**

1. The `diameter` is the largest value of `sum(max_depth_of_left_subtree, max_depth_of_right_subtree)` of all of nodes of the tree


## An Example

## Problems

### Problems - Traverse & SubTasks

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/) | 1. Traverse<br>2. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc226.go) | | 
| [116. Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/) | 1. BFS <br>2. DFS traverse with 3-nary tree | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc116.go) | | 
| [114. Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/) | 1. Sub Task idea| Definition of Recursion function | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc114.go) | | 
| - |- |- | - | - |

### Problems - Construction

>二叉树的构造问题一般都是使用「分解问题」的思路：构造整棵树 = 根节点 + 构造左子树 + 构造右子树。

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [654. Maximum Binary Tree](https://leetcode.com/problems/maximum-binary-tree/description/) | 1. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc654.go) | | 
| [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) | 1. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc105.go) | Complexity analyze | 
| [106. Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/) | 1. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc106.go) | Similar Complexity as 105 | 
| [889. Construct Binary Tree from Preorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/) | 1. Sub Task| Check if current node only has 1 child | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc889.go) | | 
| - |- |- | - | - |

**Complexity Analyse**

* [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) 

Pay attention to the `left-skewed tree` and `right-skewed tree`

| Tree Shape          | Recursive Calls | `for` Loop Work per Call | Total Complexity |
|:---------------------|:----------------|:--------------------------|:------------------|
| **Right-Skewed Tree** | O(n)          | O(1)                     | **O(n)**         |
| **Left-Skewed Tree**  | O(n)          | O(n)                     | **O(n²)**        |
| **Balanced Tree**     | O(log n)      | O(n) per level           | **O(n log n)**   |
| **Optimized (Hash Map Lookup) Right-Skewed** | O(n) | O(1)                     | **O(n)**         |
| **Optimized (Hash Map Lookup) Left-Skewed** | O(n) | O(1)                     | **O(n)**         |
| **Optimized (Hash Map Lookup) Balanced** | O(log n) | O(1)                     | **O(log n)**         |

### Problems - Ancestor Problems

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [236. Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/) | 1. post-order DFS<br>2. Track the path from root to target node and compare the slice | 1. Only 2 situations: one left, on right and one is parent of another <br> 2. The loop order of the track slice| [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc236.go) | | 
| [235. Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/) | Same solutions as 236 | 1. Utilize the character of BST | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc235.go) | | 
| [1650. Lowest Common Ancestor of a Binary Tree III](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iii/description/) | Linked list | 1. Check the public node 2 linked list | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1650.go) | | 
| [1257. Smallest Common Region](https://leetcode.com/problems/smallest-common-region/description/) | Same solutions as 1650 | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1257.go) | | 
||||| - |

### Problems - BST Problems

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [108. Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/) | | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc108.go) | | 
| [1382. Balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/description/) | in-order traverse + convert ordered array to BST | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1382.go) | | 
| [314. Binary Tree Vertical Order Traversal](https://leetcode.com/problems/binary-tree-vertical-order-traversal/description/) | | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc314.go) | | 

### BST Problems - Construction
| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/description/) | DFS post-order | How to set memo effectively | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc96.go) | | 
| [95. Unique Binary Search Trees II](https://leetcode.com/problems/unique-binary-search-trees-ii/description/) | DFS post-order | Edged case of `low > high` and `low == high` | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc95.go) | | 

Reference
1. https://labuladong.online/algo/data-structure/bst-part3/




* LC116. Populating Next Right Pointers in Each Node
    * Why the normal `traverse` approach doesn't work with this problem? O(N), O(1)
    * Util BFS `traverse`. O(N), O(N)
    * LC117. Populating Next Right Pointers in Each Node II
        * BFS approach. O(N), O(N)
        * BFS approach with cursive. O(N), O(N)
        * Multiple pointers approach & sentinel. O(N), O(Cons). And the approach also work with LC116.
* LC114. Flatten Binary Tree to Linked List
    * Traverse the tree, construct the link.
    * Flat recursively

***Construction***


### Other Problems
| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [1530. Number of Good Leaf Nodes Pairs](https://leetcode.com/problems/number-of-good-leaf-nodes-pairs/description/) | DFS | * Count the pairs of left sub-tree, right sub-tree and current node <br> * How to calculate the distance? Utilized height | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1530.go) | | 
| [993. Cousins in Binary Tree](https://leetcode.com/problems/cousins-in-binary-tree/description/) | DFS, BFS | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc993.go) | | 



### BT Problems

### BT Problems - Construction

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) | preorder inorder | Boundary of array | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc105.go) | | 


### BT Problems - Widt & Column Related

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [662. Maximum Width of Binary Tree](https://leetcode.com/problems/maximum-width-of-binary-tree/description/) | BFS | Edged case | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc662.go) | | 


**Binary Tree**

* LC106. Construct binary tree from preorder and inorder array
    * Recursively.
    * Key points
      * Bound of array
* LC654. Maximum Binary Tree
    * Recursively
* LC889. Construct binary tree from preorder and postorder array  
    * Recursively
    * Key Points
        * 2 situations
        * Common solution.
* LC652. Find Duplicate Subtrees
    * DFS. Post order
    * Key Points
        * Generate a `signature` for each sub tree
            * Serilize the tree or
            * generate an id for it. Pay attention to the id of `nil node`
        * Time: O(n). O(n), O(1)
        * Space: O(n)
* LC315. Count of Smaller Numbers After Self
    * Merge Sort
    * BIT
    * Complexity:
      * T:
        * Copy middle list: O(N)
        * Merge Sort: O(N*LogN) 
        * Setup Index Map: O(N)
        * Query and Update BIT: O(N*LogN)*2
      * Space
        * Middle list: O(N)
        * Index Map: O(N)
        * BIT: O(N)
* LC493. Reverse Pairs
    * Similar as LC315.
      * Reverse BIT
    * Solution 2. Only with Merge Sort
      * Key Points
        * Count first and then sort
        * count += middle-i+1
        * Complexity
          * T: 
            * Compare and Sort: 2(N*logN)
          * S:
            * O(N)
      * Why LC315 can not resolved with only Merge Sort?

* LC1664. Lowest Common Ancestor of a Binary Tree II.
  * Key Points.
    * Keep the idea of pre-order, in-order, post-order traverse...
* LC1676. Lowest Common Ancestor of a Binary Tree IV
  * Key Point.
    * Difference from LC1664??

**Complete Binary Tree**
  * Principle
    > According to Wikipedia, every level, except possibly the last, is completely filled in a complete binary tree, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.

    * For any node, if it has children, then, there must be at least 1 `Perfect Binary Tree` in it's children. 
    
**Perfect Binary Tree**
  * Principle
    * Every level of the tree is full
    
**Full Binary Tree**
  * Principle
    * Every node has either has both of the 2 children or none of the 2 children.
    
**Binary Search Tree**

* Key Points
  * Use closure to reduce the complexity of passing parameters
  *
* LC230. Kth Smallest Element in a BST
    * Inorder traverse
    * Follow Up
      * Extend the BST with `NumberSumOfSubtree`
      * The operation of `Insert/Delete` elements into/from BST

* LC538. LC1038. Convert BST to Greater Tree (same as 1038)
    * DFT and right sub tree first (in order)


* LC98. Validate Binary Search Tree
  * Key Points
    * Not only the left and right child. But also all the left and right subtree
* LC700. Search in a Binary Search Tree.
* LC701. Insert into a Binary Search Tree.
* LC450. Delete Node in a BST

**Binary Indexed Tree**

![](../images/tree_bit.png?raw=true)

# DFS And BFS

## Thinking Patterns - DFS v.s. Backtrack

## Problems - Islands Problems

| Problems | Possible Solutions | Key Points | Code | Similar Problems | Comments |
| :- | :- | :- |:- | :- | 
| [200. Number of Islands](https://leetcode.com/problems/number-of-islands/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc200.go) | | |
| [1254. Number of Closed Islands](https://leetcode.com/problems/number-of-closed-islands/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc1254.go) | | |
| [1905. Count Sub Islands](https://leetcode.com/problems/count-sub-islands/description/) | dfs, bfs, union-find | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc1905.go) | 1992 | |
| [1020. Number of Enclaves](https://leetcode.com/problems/number-of-enclaves/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc1020.go) | | |
| [694. Number of Distinct Islands](https://leetcode.com/problems/number-of-distinct-islands/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc694.go) | | |
| [695. Max Area of Island](https://leetcode.com/problems/max-area-of-island/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc695.go) | | |
| | | | | |- | 

**Key Points**

1. 694
    How to present the shape of islands with `BFS` and `DFS`?


**Complexity Analyze**

1. 200.

>Time Complexity
1. O(N+4N) = O(N) N = m*n
2. Loop all the node outside, m*n
3. Overall O(N)
>
Space Complexity
1. For DFS, Recursive stack depth: worst at `O(N)`
2. For BFS, Queue length: worst at `O(N)`
3. Worst case example, `m=1, n = N, and all equals 1`
4. Use `grid` as  visited, no extra spaces

2. 1254, 1905, 1020, 694

>Similar as 200



## BFS

### Thinking Patterns

>1. BFS算法的本质就是二叉树的层序遍历。
>
>2. 衍生到多叉树的层序遍历，和图的遍历（增加visited数组）
>
>3. BFS 算法经常用来求解最短路径问题。最短路径，都可以类比成二叉树最小深度问题（寻找距离根节点最近的叶子节点），递归遍历必须要遍历整棵树的所有节点才能找到目标节点，而层序遍历不需要遍历所有节点就能搞定，所以层序遍历适合解决最短路径问题。
>

### BFS Problems 

| Problems | Possible Solutions | Key Points | Code | Similar Problems | Comments |
| :- | :- | :- |:- | :- | 
| [773. Sliding Puzzle](https://leetcode.com/problems/sliding-puzzle/description/) | bfs | | [code](https://github.com/brofu/leetcode/blob/main/bfs/bfs_lc773.go) | | |
| [752. Open the Lock](https://leetcode.com/problems/open-the-lock/description/) | bfs | | [code](https://github.com/brofu/leetcode/blob/main/bfs/bfs_lc752.go) | | |
| [919. Complete Binary Tree Inserter](https://leetcode.com/problems/complete-binary-tree-inserter/description/) | bfs | | [code](https://github.com/brofu/leetcode/blob/main/bfs/bfs_lc919.go) | | |
| [841. Keys and Rooms](https://leetcode.com/problems/keys-and-rooms/description/) | bfs | | [code](https://github.com/brofu/leetcode/blob/main/bfs/bfs_lc841.go) | | |
| [433. Minimum Genetic Mutation](https://leetcode.com/problems/minimum-genetic-mutation/description/) | bfs | | [code](https://github.com/brofu/leetcode/blob/main/bfs/bfs_lc433.go) | | |
| [1926. Nearest Exit from Entrance in Maze](https://leetcode.com/problems/nearest-exit-from-entrance-in-maze/description/) | bfs | | [code](https://github.com/brofu/leetcode/blob/main/bfs/bfs_lc1926.go) | | |
| [1091. Shortest Path in Binary Matrix](https://leetcode.com/problems/shortest-path-in-binary-matrix/description/) | bfs | | [code](https://github.com/brofu/leetcode/blob/main/bfs/bfs_lc1091.go) | | |
| | | | | |- | 

### Complexity Analyze

Refer to the code

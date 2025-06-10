# DFS And BFS

## Thinking Patterns - DFS v.s. Backtrack

## Problems - Islands Problems

| Problems | Possible Solutions | Key Points | Code | Similar Problems | Comments |
| :- | :- | :- |:- | :- | 
| [200. Number of Islands](https://leetcode.com/problems/number-of-islands/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc200.go) | | |
| [1254. Number of Closed Islands](https://leetcode.com/problems/number-of-closed-islands/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc1254.go) | | |
| [1905. Count Sub Islands](https://leetcode.com/problems/count-sub-islands/description/) | dfs, bfs, union-find | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc1905.go) | 1992 | |
| [1020. Number of Enclaves](https://leetcode.com/problems/number-of-enclaves/description/) | dfs, bfs | | [code](https://github.com/brofu/leetcode/blob/main/dfs/dfs_lc1020.go) | | |
| | | | | |- | 

**Complexity Analyze**

200.

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

1254

>Similar as 200

1905

>Similar as 200

1905

>Similar as 200

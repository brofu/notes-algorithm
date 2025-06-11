## Basic Graph Problems

* DG Cycle Detection (Directed Graph)
* Topological Sorting (Directed Graph)
* Bipartite Graph (Un-Directed Graph)

### Problems - DG Cycle Detection (Directed Graph)

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [207. Course Schedule](https://leetcode.com/problems/course-schedule/description/) | 1. DFS<br> 2. BFS | 1. DFS. The order of `checking onPath` and `visited`<br> 2. The key idea of BFS. Refer to the code | [code](https://github.com/brofu/leetcode/blob/main/graph/graph_lc207.go) | | 
| - |- |- | - | - |


### Problems - Topological Sorting (Directed Graph)

**DFS**

>把图结构后序遍历的结果(进行反转)，就是拓扑排序的结果。
>
>二叉树的后序遍历是什么时候？遍历完左右子树之后才会执行后序遍历位置的代码。换句话说，当左右子树的节点都被装到结果列表里面了，根节点才会被装进去。
>
>后序遍历的这一特点很重要，之所以拓扑排序的基础是后序遍历，是因为一个任务必须等到它依赖的所有任务都完成之后才能开始开始执行。

**BFS**

>BFS 算法借助`indegree`数组记录每个节点的入度
>节点的遍历顺序就是拓扑排序的结果。
>通过`indegree`数组实现visited数组的作用，只有入度为0的节点才能入队，保证不会出现死循环。

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [210. Course Schedule II](https://leetcode.com/problems/course-schedule-ii/description/) | 1. DFS <br> 2. BFS | 1. DFS. The order of `checking onPath` and `visited`<br> 2. The key idea of BFS | [code](https://github.com/brofu/leetcode/blob/main/graph/graph_lc210.go) | | 
| - |- |- | - | - |


### Problems - Bipartite Graph (UnDirected Graph)

An example of `Bipartite Graph` in real world is to present the relationship between `actors` and `movies`

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [785. Is Graph Bipartite?](https://leetcode.com/problems/is-graph-bipartite/description/) | 1. DFS <br> 2. BFS | For BFS, note the difference from `Cycyle Detection` and `Topological Sorting` | [code](https://github.com/brofu/leetcode/blob/main/graph/graph_lc785.go) | | 
| [886. Possible Bipartition](https://leetcode.com/problems/possible-bipartition/description/) | 1. DFS <br> 2. BFS | For BFS, note the difference from `Cycyle Detection` and `Topological Sorting` | [code](https://github.com/brofu/leetcode/blob/main/graph/graph_lc886.go) | | 
| - |- |- | - | - |


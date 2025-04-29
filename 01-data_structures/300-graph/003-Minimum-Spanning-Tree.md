## Minimum Spanning Tree - Un-Directed Weighted Graph

### Concepts

>树就是`无环连通图`。
>图的生成树,就是在图中找一棵包含图中的所有节点的树。`生成树是含有图中所有顶点的无环连通子图`。
>最小生成树是所有可能生成树中，权重和最小的那棵生成树。

>一般来说，都是在无向加权图中计算最小生成树. 使用最小生成树算法的现实场景中，图的边权重一般代表成本、距离这样的标量。


### Kruskal Algorithm

`Greedy` + `Union-Find`

>主要思路利用Union-Find并查集算法向最小生成树中添加边，配合排序的贪心思路，从而得到一棵权重之和最小的生成树。
>
>复杂度分析
>
>空间复杂度O(V+E)
>
> 时间复杂度主要耗费在排序，需要O(ElogE)


### Prim Algorithm

>**切分定理**
>
>对于任意一种「切分」，其中权重最小的那条「横切边」一定是构成最小生成树的一条边。

>Prim 算法的逻辑是，每次切分都能找到最小生成树的一条边，然后又可以进行新一轮切分，直到找到最小生成树的所有边为止。

>**关键点**
>
>节点去重，防止出现环
>Priority Queue

>**时间复杂度**
>
>主要在优先级队列pq的操作上，由于pq里面装的是图中的「边」，假设一幅图边的条数为E那么最多操作O(E) pq。每次操作优先级队列的时间复杂度取决于队列中的元素个数，取最坏情况就是O(logE)。
>
>Kruskal 算法，它的时间复杂度主要是给所有边按照权重排序，也是 

### Problems

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [1135. Connecting Cities With Minimum Cost](https://leetcode.com/problems/connecting-cities-with-minimum-cost/description/) |`Kruskal`| | [code](https://github.com/brofu/leetcode/blob/main/graph/mst/mst_lc1135.go) | | 
| [1584. Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/description/) |1. `Kruskal`<br> 2. `Prim` <br> 3. `Prim` with optimization | Refer to the code | [code](https://github.com/brofu/leetcode/blob/main/graph/mst/mst_lc1584.go) |1. O(N^2logN)<br> 2. O(N^2logN)<br>3. O(N^2)| 
| - |- |- | - | - |



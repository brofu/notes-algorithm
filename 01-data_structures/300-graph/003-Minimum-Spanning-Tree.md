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


### Problems

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [1135. Connecting Cities With Minimum Cost](https://leetcode.com/problems/connecting-cities-with-minimum-cost/description/) |`Kruskal`| | [code](https://github.com/brofu/leetcode/blob/main/graph/mst/mst_lc1135.go) | | 
| [1584. Min Cost to Connect All Points](https://leetcode.com/problems/min-cost-to-connect-all-points/description/) |1. `Kruskal`<br> 2. `Prim`| Refer to the code | [code](https://github.com/brofu/leetcode/blob/main/graph/mst/mst_lc1584.go) | | 
| - |- |- | - | - |



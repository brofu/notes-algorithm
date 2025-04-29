## Shorted Path - Directed Weighted Graph

### Dijkstra Algorithm

**Key Idea**

1. `Greedy`. Utilize `Priority Queue`, to find the NEAREST node SO FAR. And calculate distance (from `start`) to the neighbors of it. If there is SMALLER distance, update, and push that neighbor into the `Priority Queue`
2. With `BFS` style

**Time Complexity** 

* O(ElogV)
    * Each `V` should enter the PQ at least ONCE.
    * For each `V`, need to calculate NEW distance (to the `start`)
    * Finally, around O(ElogV)

**Pre-Condition to Utilize Dijkstra**

1. Directed Weighted graph
2. No negative weight

#### Problems

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [743. Network Delay Time](https://leetcode.com/problems/network-delay-time/description/) | Dijkstra| | [code](https://github.com/brofu/leetcode/blob/main/graph/graph_lc743.go) | | 
| [1631. Path With Minimum Effort](https://leetcode.com/problems/path-with-minimum-effort/description/) | Dijkstra| How to define and update the `effortToNode` array? | [code](https://github.com/brofu/leetcode/blob/main/graph/dijkstra/dijkstra_lc1631.go) | | 
| - |- |- | - | - |



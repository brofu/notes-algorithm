# Backtrack

## Thinking Patterns

>抽象地说，解决一个回溯问题，实际上就是遍历一棵决策树的过程，树的每个叶子节点存放着一个合法答案。把整棵树遍历一遍，把叶子节点上的答案都收集起来，就能得到所有的合法答案。
>
>站在回溯树的一个节点上，只需要思考3个问题：
>
1. 路径. 也就是已经做出的选择。
>
2. 择列表. 也就是当前可以做的选择。
>
3. 结束条件. 也就是到达决策树底层，无法再做选择的条件。


## Code Template

```
result = []

def backtrack(path, choices_list):
    if can_finish:
        result.add(path)
        return
    
    for choice in choinces_list:
        choose a choice // usually need to update the `path`
        backtrack(path, new_choice_list)
        cancel the choice // revert the updating to `path`
```

## Problems

### Problems - Permutation, Combination and Set Problems

Generally, there are 3 types of classic problems for `Permutation`, `Combination` and `Set` problems. There maybe some other variants from these 3 types.

    1. Choose from a list which contains `Non-Duplicate` elements, and element can ONLY be used for ONE time.
    2. Choose from a list which contains `Duplicate` elements, and element can ONLY be used for ONE times.
    3. Choose from a list which contains `Non-Duplicate` elements, and element can be used for MULTIPLE times.

**Thinking Patterns**

And the key points of these problems is the `backtrack tree`


**Problems**

| Types | Problems | Key Points | Possible Solutions | Comments |
| :- | :- | :- |:- | :- | 
| Permutation Problems | [46](https://leetcode.com/problems/permutations/description/) | | [code](backtrack_lc46.go) | type 1 | 
| Permutation Problems | [47](https://leetcode.com/problems/permutations-ii/description/) | | [code](backtrack_lc47.go) | type 2 | 
| Combination Problems | [77](https://leetcode.com/problems/combinations/description/)  | |[code](backtrack_lc77.go) | type 1 | 
| Combination Problems | [216](https://leetcode.com/problems/combination-sum-iii/description/)  | |[code](backtrack_lc216.go) | type 1 | 
| Combination Problems | [40](https://leetcode.com/problems/combination-sum-ii/description/)  | |[code](backtrack_lc40.go) | type 2 | 
| Combination Problems | [39](https://leetcode.com/problems/combination-sum/description/)  | |[code](backtrack_lc39.go) | type 3 | 
| Set Problems | [78. Subsets](https://leetcode.com/problems/subsets/description/)  | |[code](backtrack_lc78.go) | type 1 | 
| Set Problems | [90](https://leetcode.com/problems/subsets-ii/description/)  | |[code](backtrack_lc90.go) | type 2 | 
| | | || -| 

**Notes**
1. About `Set Problems`. 
   * How to abstract the 3 core questions about the backtrack framework

### Problems - Variants Problems

| Types | Problems | Key Points | Possible Solutions | Comments |
| :- | :- | :- |:- | :- | 
| Debt Problem | [465](https://leetcode.com/problems/optimal-account-balancing/description/) | | [code](backtrack_lc465.go) | | 

**References**

1. https://labuladong.online/algo/essential-technique/backtrack-framework/ 
2. https://labuladong.online/algo/essential-technique/permutation-combination-subset-all-in-one/
3. https://labuladong.online/algo/practice-in-action/two-views-of-backtrack/


### Problems - Others

**Problems**

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [494. Target Sum](https://leetcode.com/problems/target-sum/description/) | 1. Backtrack <br> 2. DP | 1. Pruning with memo | [code](https://github.com/brofu/leetcode/blob/main/backtrack/backtrack_lc494.go) | | 
| [37. Sudoku Solver](https://leetcode.com/problems/sudoku-solver/description/) | backtrack | How to control the flow? Refer to the code | [code](https://github.com/brofu/leetcode/blob/main/backtrack/backtrack_lc37.go) | | 
| [51. N-Queens](https://leetcode.com/problems/n-queens/description/) | backtrack | How to control the flow? N-Queen v.s. Sudoku Problem | [code](https://github.com/brofu/leetcode/blob/main/backtrack/backtrack_lc51.go) | | 
| [52. N-Queens II](https://leetcode.com/problems/n-queens-ii/description/) | backtrack | | [code](https://github.com/brofu/leetcode/blob/main/backtrack/backtrack_lc52.go) | | 
| | | | |- | 

**Notes**
1. More about the **N-Queen** problems
    * Time Complexity
        * O(N^N) ==> O(N!) with O(1) prune algorithm
        * `cols`, `diag1` and `diag2`
    * Space Complexity 
        * O(N^2) if store the location data with `board` (n * n matrix)
        * O(N) with `cols`, `diag1`, and `diag2`
    * How does `cols`, `diag1`, `diag2` work?
        * 主对角线的特点：所有在同一主对角线上的格子都满足： `row − col = 常数`  
        * 但 row - col 的范围是从 − 𝑁 + 1 到 𝑁 − 1 不能直接作为数组下标 
        * 所以我们统一加上偏移 𝑁 − 1 把范围映射到 [0, 2N-2]

**References**
1. https://labuladong.online/algo/dynamic-programming/target-sum/





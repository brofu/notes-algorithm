# Dynamic Programming

## Key Points

1. 最优子结构
    * If there is 最优子结构
    
2. 状态转移方程
    * (Recurrence or Recursion) 前后项之前关联+base case的描述
    * Examples:
        * Fibonacci Problems: https://labuladong.github.io/algo/images/%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%E8%AF%A6%E8%A7%A3%E8%BF%9B%E9%98%B6/fib.png
        * Coins Change Problem: https://labuladong.github.io/algo/images/%E5%8A%A8%E6%80%81%E8%A7%84%E5%88%92%E8%AF%A6%E8%A7%A3%E8%BF%9B%E9%98%B6/coin.png
        
3. Overlapping sub problems. For example, `Fibonacci Number`
    * Solution:  Cache the middle result
    * Optimization: Space used by Cache

4. Memorization or Tabulation. 
    * LC300. `dp[i]`, the length of longest sub sequence ends with `nums[i]` in `nums`
5. Formulation of State Transition Equation 
    * LC300. `dp[i] = max(dp[i], dp[j])+1), where j = [i-1,i-2,…,0] && nums[j] < nums[i]`


## Thinking Patterns

> 动态规划不就是从最简单的 base case 往后推导吗，可以想象成一个链式反应，以小博大。但只有符合最优子结构的问题，才有发生这种链式反应的性质。 找最优子结构的过程，其实就是证明状态转移方程正确性的过程，方程符合最优子结构就可以写暴力解了，写出暴力解就可以看出有没有重叠子问题了，有则优化，无则 OK。这也是套路，经常刷题的读者应该能体会。


## An Example

Use problem [LC322](https://leetcode.com/problems/coin-change/description/) as an example. 

**最优子结构**

>这个问题是动态规划问题，因为它具有「最优子结构」的.要符合「最优子结构」，子问题间必须互相独立。
>
>回到凑零钱问题，为什么说它符合最优子结构呢？ 假设你有面值为 1, 2, 5 的硬币，你想求 amount = 11 时的最少硬币数（原问题），如果你知道凑出 amount = 10, 9, 6 的最少硬币数（子问题），你只需要把子问题的答案加一（再选一枚面值为 1, 2, 5 的硬币），求个最小值，就是原问题的答案。因为硬币的数量是没有限制的，所以子问题之间没有相互制，是互相独立的。


**状态转移方程**

> 那么，既然知道了这是个动态规划问题，就要思考如何列出正确的状态转移方程？
>
>1、确定「状态」，也就是原问题和子问题中会变化的变量。由于硬币数量无限，硬币的面额也是题目给定的，只有目标金额会不断地向 base case 靠近，所以唯一的「状态」就是目标金额 amount。
>
>2、确定「选择」，也就是导致「状态」产生变化的行为。目标金额为什么变化呢，因为你在选择硬币，你每选择一枚硬币，就相当于减少了目标金额。所以说所有硬币的面值，就是你的「选择」。
>
>3、明确 dp 函数(Top to Down)/dp数组(Down to Top)的定义。

> Top to Down 
>
> 我们这里讲的是自顶向下的解法，所以会有一个递归的 dp 函数，一般来说函数的参数就是状态转移中会变化的量，也就是上面说到的「状态」；函数的返回值就是题目要求我们计算的量。就本题来说，状态只有一个，即「目标金额」，题目要求我们计算凑出目标金额所需的最少硬币数量。
>
>所以我们可以这样定义 dp 函数：dp(n) 表示，输入一个目标金额 n，返回凑出目标金额 n 所需的最少硬币数量。

> Down to Top
>
>当然，我们也可以自底向上使用 dp table 来消除重叠子问题，关于「状态」「选择」和 base case 与之前没有区别，dp 数组的定义和刚才 dp 函数类似，也是把「状态」，也就是目标金额作为变量。不过 dp 函数体现在函数参数，而 dp 数组体现在数组索引：
>
>dp 数组的定义：当目标金额为 i 时，至少需要 dp[i] 枚硬币凑出。


## Problems

There are some types, classic dp problems, such as 
* Sub Sequence Problems
* Knapsack Problems
* Greedy Related Problems

### Problems - Sub Sequences 

**Thinking Patterns**

Usually there **2 templates** for `sub sequences problems`, 

> 一个一维的 dp 数组：
> ```
> int n = array.length;
> int[] dp = new int[n];
> for (int i = 1; i < n; i++) {
>    for (int j = 0; j < i; j++) {
>        dp[i] = 最值(dp[i], dp[j] + ...)
>    }
> }
> ```
> `最长递增子序列` 和 `最大子数组和` 都是这个思路。
>
> 在这个思路中 dp 数组的定义是：
>
> **在子数组arr[0..i]中，以arr[i]结尾的子序列的(最值)长度是dp[i]** ==> Why not define it as `the LIS of arr[0...i]? Refer to 1.
>
> For example, `300. Longest Increasing Subsequence` and `53. Maximum Subarray`
>
> 第二种思路模板是一个二维的 dp 数组：
>
> ```
> n := len(arr)
> dp := make([][]int, n)
> // 初始化 dp 数组
> for i := 0; i < n; i++ {
>     dp[i] = make([]int, n)
>     for j := 0; j < n; j++ {
>         if arr[i] == arr[j] {
>             // 当 arr[i] 与 arr[j] 相等时，可以做出选择，做出选择的结果是...
>             dp[i][j] = dp[i][j] + ...
>         } else {
>             // 当 arr[i] 与 arr[j] 不相等时，可以做出选择，做出选择的结果是 ...
>             dp[i][j] = min(...)
>         }
>     }
> }
> ```
> 涉及两个字符串/数组的场景，dp 数组的定义如下：
>
> **在子数组arr1[0..i]和子数组arr2[0..j]中，我们要求的子序列长度为dp[i][j]**
>
> For example, `1143. Longest Common Subsequence` and `72. Edit Distance`
>
> 只涉及一个字符串/数组的场景，dp 数组的定义如下：
>
> 在 子数组 array[i..j] 中，我们要求的子序列的长度为 dp[i][j]。
> 
> For example, `516. Longest Palindromic Subsequence`


**Problems**

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [673. Number of Longest Increasing Subsequence](https://leetcode.com/problems/number-of-longest-increasing-subsequence/description/) | 1. DP <br> 2. BIT | 1. DP <br> * How to setup/update dp array for `dpCount`? | [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc2263.go) | | 
| [300. Longest Increasing Subsequence](https://leetcode.com/problems/longest-increasing-subsequence/description/) | * DP | * How to define the dp table <br>* Compress space complexity | [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc300.go) | | 
| [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/description/) | 1. DP <br>2. Sliding Window <br> 3. Prefix Sum | * How to define the dp table <br>* Compress space complexity | [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc53.go) | | 
| [72. Edit Distance](https://leetcode.com/problems/edit-distance/description/) | 1. DP table 2-D DP table <br> 2. DP function | * How to define dp function<br>* How to define DP table <br>* how to compress space with O(N)| [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc72.go) | | 
| [1143. Longest Common Subsequence](https://leetcode.com/problems/longest-common-subsequence/description/) | 1. DP table 2-D DP table <br> 2. DP function | * How to define dp function<br>* How to define DP table <br>* how to compress space with O(N)* DP 2-D DP table| [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc1143.go) | Almost same as problem 72.| 
| [583. Delete Operation for Two Strings](https://leetcode.com/problems/delete-operation-for-two-strings/description/) | 1. DP table 2-D DP table <br> 2. DP function | * The problem is actually to calculate the LCS of two strings. | [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc583.go) | Almost same as problem 1143.| 
| [712. Minimum ASCII Delete Sum for Two Strings](https://leetcode.com/problems/minimum-ascii-delete-sum-for-two-strings/description/) | 1. DP function. <br> 2. DP 2-D table. <br> 3. DP 1-D table. | * dp[i][j] means min sum of s1[0...i] and s2[0...j] | [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc712.go) | Use DP table record the sum | 



**Reference**
1. https://labuladong.online/algo/dynamic-programming/maximum-subarray/


### Problems - Knapsack Problems

**Thinking Patterns**

How connect `Knapsack Problems` with `Dynamic Programming` framework?

a. `Status` and `Choice`

> 先说状态，如何才能描述一个问题局面？只要给几个物品和一个背包的容量限制，就形成了一个背包问题呀。所以状态有两个，就是「背包的容量」和「可选择的物品」。
>
> 再说选择，也很容易想到啊，对于每件物品，你能选择什么？选择就是「装进背包」或者「不装进背包」。
>
> 明白了状态和选择，动态规划问题基本上就解决了，对于自底向上的思考方式，代码的一般框架是这样：
> 
> ```
> for 状态1 in 状态1的所有取值：
>   for 状态2 in 状态2的所有取值：
>      for ...
>            dp[状态1][状态2][...] = 择优(选择1，选择2...)
> ```

b. Definition of `DP table`

> 首先看看刚才找到的「状态」，有两个，也就是说我们需要一个二维dp数组。
>
> dp[i][w]的定义如下：对于前i个物品，当前背包的容量为w，这种情况下可以装的最大价值是dp[i][w]。
>
> 比如说，如果dp[3][5] = 6，其含义为：对于给定的一系列物品中，若只对前3个物品进行选择，当背包容量为5时，最多可以装下的价值为6。
>
> 根据这个定义，我们想求的最终答案就是 dp[N][W]。base case 就是 dp[0][..] = dp[..][0] = 0，因为没有物品或者背包没有空间的时候，能装的最大价值就是0。
>
> ```
> int[][] dp[N+1][W+1]
> dp[0][..] = 0
> dp[..][0] = 0
>
> for i in [1..N]:
    for w in [1..W]:
>         dp[i][w] = max(
            把物品 i 装进背包,
>           不把物品 i 装进背包
        )
> return dp[N][W]
> ```

c. How does the `status` change based on the `choice`?

> 如果没有把这第 i 个物品装入背包，那么很显然，最大价值 dp[i][w] 应该等于 dp[i-1][w]，继承之前的结果。

> 如果把这第 i 个物品装入了背包，那么 dp[i][w] 应该等于 val[i-1] + dp[i-1][w - wt[i-1]]。
>
> 首先，由于数组索引从0开始，而我们定义中的i是从1开始计数的，所以val[i-1]和wt[i-1]表示第i个物品的价值和重量。
> 
> 如果选择将第i个物品装进背包，那么第i个物品的价值val[i-1] 肯定就到手了，接下来你就要在剩余容量w-wt[i-1]的限制下，在前i-1个物品中挑选，求最大价值，即dp[i-1][w - wt[i-1]]。
>
> code about the `status` change
> ```
> for i in [1..N]:
>   for w in [1..W]:
>        dp[i][w] = max(
>           dp[i-1][w],
>           dp[i-1][w - wt[i-1]] + val[i-1]
>       )
> return dp[N][W]
> ```

d. Finally, we got the code framework for `0-1 Knapsack Problem`

```
func knapsack(wt, val []int) int {
    // base case 已初始化
    dp := make([][]int, len(wt)+1)
    for i := range dp {
        dp[i] = make([]int, len(wt)+1)
    }
    for i := 1; i <= len(wt)+1; i++ {
        for w := 1; w <= len(wt)+1; w++ {
            if w-wt[i-1] < 0 { // bag space NOT enough
                dp[i][w] = dp[i-1][w]
            } else { // choice to or NOT to put wt[i-1] into bag
                dp[i][w] = max(
                    dp[i-1][w-wt[i-1]]+val[i-1],
                    dp[i-1][w],
                )
            }
        }
    }
    return dp[N][W]
}

func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}
```


| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [416. Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/description/) | 1. 2-D DP table <br> 2. 1-D DP table | * How to connect the problem with `Knapsack Problem`? | [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc416.go) | - | 
| [518. Coin Change II](https://leetcode.com/problems/coin-change-ii/description/) | 1. 2-D DP table <br> 2. 1-D DP table | * The difference from `change coin I` | [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc518.go) | - | 
| [494. Target Sum](https://leetcode.com/problems/target-sum/description/) | 1. 2-D DP <br> 2. 1-D DP table <br> 3. Backtrack | * The base case. dp[1...N][0] not equal to 0| [code](https://github.com/brofu/leetcode/blob/main/dp/dp_lc494.go) | - | 



**References**
1. [0-1 Knapsack Problem.](https://labuladong.online/algo/dynamic-programming/knapsack1/)
2. [Subset Knapsack Problem](https://labuladong.online/algo/dynamic-programming/knapsack2/)
3. [Complete Knapsack Problem](https://labuladong.online/algo/dynamic-programming/knapsack3/)
4. https://labuladong.online/algo/dynamic-programming/target-sum/






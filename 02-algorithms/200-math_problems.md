# Math Related Problems

## Key Points

* Edged Case
    * Case of `overflow`
    
* Performance
    * Utilize `bit operation` for `Power` calculation.
    

## Problems

### Problems - Mod & Power Problems

**Key Points**

* About `Mod`. `A*B % k = (A % k) * (B % k) % K`
* Quick `Power`, for `Power(x, n)`. O(N) => O(lgN)
    * if `n % 2 == 1`, => `x * Power(x, n-1)`
    * if `n % 2 == 0`, => `Power(Power(x, n/2), 2)`

**Problems**

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [50. Pow(x, n)](https://leetcode.com/problems/powx-n/description/) | | 1. If `n == math.MinInt32` <br> 2. If n is very large, how to reduce the time complexity? | [code](https://github.com/brofu/leetcode/blob/main/math/math_lc50.go) |-| 
| [372. Super Pow](https://leetcode.com/problems/super-pow/description/) | |1. `Iteration` or `Recursion` for the array.<br> 2. Utilize `bit operation` for `Power` calculation | [code](https://github.com/brofu/leetcode/blob/main/math/math_lc372.go) |-| 


### References
1. [Mod Problems](https://leetcode.com/problems/super-pow/description/)

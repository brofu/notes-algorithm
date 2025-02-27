### Problems - Complete Tree Problems

Note the definition of `Complete Tree` and `Perfect Tree`

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [222. Count Complete Tree Nodes](https://leetcode.com/problems/count-complete-tree-nodes/description/) | Sub task. Combine the normal tree and `perfect tree` | How to calculate the time complexity| [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc222.go) |O(lgN*logN) | 
||||| - |

**Time Complexity Analyze** 

Let's consider a `complete tree` with N nodes.

Since ONE sub tree of a `complete tree` must be a `perferect tree`, so we have

<div class="katex-display">
$$ 
T(N) = O(lgN) + T(N/2)
$$   
</div>

For the `perfect` sub tree, we have `O(lgN)`, and the other sub tree, there is `T(N/2)`. And similarly, we have

<div class="katex-display">
$$T(N/2) = O(lg(N/2)) + T(N/4)$$ 
</div>
<div class="katex-display">
$$T(N/4) = O(lg(N/4)) + T(N/8)$$
</div>
<div class="katex-display">
$$......$$
</div>

So, we actually have 

<div class="katex-display">
$$T(N) = O(lgN) + T(N/2)$$ 
</div>
<div class="katex-display">
$$= O(lgN) + O(lg(N/2)) + T(N/4)$$
</div>
<div class="katex-display">
$$= O(lgN) + O(lg(N/2)) + O(lg(N/4)) + T(N/8)$$
</div>
<div class="katex-display">
$$= O(lg(N/2^0)) + O(lg(N/2^1)) + O(lg(N/2^2)) + ...... + O(lg(N/2^i))$$
</div>
<div class="katex-display">
$$= O(lgN - 0) + O(lgN - 1) + O(lgN - 2) + ...... + O(lgN - i)$$ 
</div>

As we know, the max value of `i` is `lgN`, so we have 

<div class="katex-display">
$$T(N) = O(lgN) + O(lgN) - O(1) + O(lgN) - O(lgN) - O(2) + ...... O(lgN) - O(lgN)$$
</div>
<div class="katex-display">
$$= O((0 + lgN)(lgN+1)/2)$$ 
</div>
<div class="katex-display">
$$= O(lgN*lgN)$$
</div>



## Tree Basic Problems

### Problems - Traverse & SubTasks

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [226. Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/description/) | 1. Traverse<br>2. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc226.go) | | 
| [116. Populating Next Right Pointers in Each Node](https://leetcode.com/problems/populating-next-right-pointers-in-each-node/description/) | 1. BFS <br>2. DFS traverse with 3-nary tree | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc116.go) | | 
| [114. Flatten Binary Tree to Linked List](https://leetcode.com/problems/flatten-binary-tree-to-linked-list/description/) | 1. Sub Task idea| Definition of Recursion function | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc114.go) | | 
| [257. Binary Tree Paths](https://leetcode.com/problems/binary-tree-paths/description/) | Traverse + DFS | how to record the trace. | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc257.go) | | 
| [129. Sum Root to Leaf Numbers](https://leetcode.com/problems/sum-root-to-leaf-numbers/description/) | Traverse + DFS | Similar with 257 | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc129.go) | | 
| [199. Binary Tree Right Side View](https://leetcode.com/problems/binary-tree-right-side-view/description/) | Traverse + BFS or DFS| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc199.go) | | 
| [662. Maximum Width of Binary Tree](https://leetcode.com/problems/maximum-width-of-binary-tree/description/) | Traverse + BFS | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc662.go) | | 
| [988. Smallest String Starting From Leaf](https://leetcode.com/problems/smallest-string-starting-from-leaf/description/) | Traverse + DFS | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc988.go) | | 
| [1022. Sum of Root To Leaf Binary Numbers](https://leetcode.com/problems/sum-of-root-to-leaf-binary-numbers/description/) | Traverse + DFS | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1022.go) | | 
| [1457. Pseudo-Palindromic Paths in a Binary Tree](https://leetcode.com/problems/pseudo-palindromic-paths-in-a-binary-tree/description/) | Traverse + DFS | bit operation to check if a path is pseudo-palindromic. refer to the code | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1457.go) | | 
| - |- |- | - | - |


### Problems - Sub Tasks

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) | Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc105.go) | | 
| [106. Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/) | Sub Task| HashMap to reduce time complexity| [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc106.go) | | 
| [889. Construct Binary Tree from Preorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/) | Sub Task| 1. HashMap to reduce time complexity<br>2. Use slice index | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc889.go) | | 
| - |- |- | - | - |


### Problems - Construction

>二叉树的构造问题一般都是使用「分解问题」的思路：构造整棵树 = 根节点 + 构造左子树 + 构造右子树。

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [654. Maximum Binary Tree](https://leetcode.com/problems/maximum-binary-tree/description/) | 1. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc654.go) | | 
| [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) | 1. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc105.go) | Complexity analyze | 
| [106. Construct Binary Tree from Inorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-inorder-and-postorder-traversal/description/) | 1. Sub Task| | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc106.go) | Similar Complexity as 105 | 
| [889. Construct Binary Tree from Preorder and Postorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-postorder-traversal/description/) | 1. Sub Task| Check if current node only has 1 child | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc889.go) | | 
| - |- |- | - | - |

**Complexity Analyse**

* [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) 

Pay attention to the `left-skewed tree` and `right-skewed tree`

| Tree Shape          | Recursive Calls | `for` Loop Work per Call | Total Complexity |
|:---------------------|:----------------|:--------------------------|:------------------|
| **Right-Skewed Tree** | O(n)          | O(1)                     | **O(n)**         |
| **Left-Skewed Tree**  | O(n)          | O(n)                     | **O(n²)**        |
| **Balanced Tree**     | O(log n)      | O(n) per level           | **O(n log n)**   |
| **Optimized (Hash Map Lookup) Right-Skewed** | O(n) | O(1)                     | **O(n)**         |
| **Optimized (Hash Map Lookup) Left-Skewed** | O(n) | O(1)                     | **O(n)**         |
| **Optimized (Hash Map Lookup) Balanced** | O(log n) | O(1)                     | **O(n)**         |

### Problems - Serialization

>什么样的序列化的数据可以反序列化出唯一的一棵二叉树？
>
>当二叉树中节点的值不存在重复时：
>
如果序列化结果中不包含空指针，只给出一种遍历顺序，那么无法还原出唯一的一棵二叉树。
>
如果序列化结果中不包含空指针的信息，且给出两种遍历顺序，分两种情况：
>
* 如果给出的是前序和中序，或者后序和中序，那么可以还原出唯一的一棵二叉树。
>
* 如果给出前序和后序，那么无法还原出唯一的一棵二叉树。
>
如果你的序列化结果中包含空指针的信息，且只给出一种遍历顺序，也要分两种情况：
>
* 如果给出的是前序或者后序，那么可以还原出唯一的一棵二叉树。
>
* 如果给出的是中序，那么无法还原出唯一的一棵二叉树。


| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [297. Serialize and Deserialize Binary Tree](https://leetcode.com/problems/serialize-and-deserialize-binary-tree/description/) | 1. Sub Task<br>2. BFS| 1. The return value of traverse function<br>2. Same approach to deserialize | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc297.go) | O(N)| 
| - |- |- | - | - |

### Problems - Ancestor Problems

| Problems | Solutions | Key Points | code| Complexity |
| :- |:- |:- | :- | :-- |
| [236. Lowest Common Ancestor of a Binary Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree/description/) | 1. post-order DFS<br>2. Track the path from root to target node and compare the slice | 1. Only 2 situations: one left, on right and one is parent of another <br> 2. The loop order of the track slice| [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc236.go) | | 
| [1676. Lowest Common Ancestor of a Binary Tree IV](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iv/description/) |Same as 236 |Note: these 2 questions require the node MUST in the tree | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1676.go) | | 
| [1644. Lowest Common Ancestor of a Binary Tree II](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-ii/description/) |Sub Task.|Note: p,q NOT necessary int the tree. So, need to make sure EACH node is traversed to check if it exists. So, put logic `root.Value == p.Value or root.Value == q.Value` to the `post-order` location | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1644.go) | | 
| [235. Lowest Common Ancestor of a Binary Search Tree](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/description/) | 1.Sub task.<br>2. Iteration| 1. Utilize the character of BST | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc235.go) |1. O(N), O(N)<br>2. O(N), O(1) | 
| [1650. Lowest Common Ancestor of a Binary Tree III](https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-tree-iii/description/) | Linked list | 1. Check the public node 2 linked list | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1650.go) | | 
| [1257. Smallest Common Region](https://leetcode.com/problems/smallest-common-region/description/) | Same solutions as 1650 | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1257.go) | | 
||||| - |

### Problems - BST Problems

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [108. Convert Sorted Array to Binary Search Tree](https://leetcode.com/problems/convert-sorted-array-to-binary-search-tree/description/) | | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc108.go) | | 
| [1382. Balance a Binary Search Tree](https://leetcode.com/problems/balance-a-binary-search-tree/description/) | in-order traverse + convert ordered array to BST | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1382.go) | | 
| [314. Binary Tree Vertical Order Traversal](https://leetcode.com/problems/binary-tree-vertical-order-traversal/description/) | | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc314.go) | | 

### BST Problems - Construction
| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/description/) | DFS post-order | How to set memo effectively | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc96.go) | | 
| [95. Unique Binary Search Trees II](https://leetcode.com/problems/unique-binary-search-trees-ii/description/) | DFS post-order | Edged case of `low > high` and `low == high` | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc95.go) | | 

Reference
1. https://labuladong.online/algo/data-structure/bst-part3/


* LC116. Populating Next Right Pointers in Each Node
    * Why the normal `traverse` approach doesn't work with this problem? O(N), O(1)
    * Util BFS `traverse`. O(N), O(N)
    * LC117. Populating Next Right Pointers in Each Node II
        * BFS approach. O(N), O(N)
        * BFS approach with cursive. O(N), O(N)
        * Multiple pointers approach & sentinel. O(N), O(Cons). And the approach also work with LC116.
* LC114. Flatten Binary Tree to Linked List
    * Traverse the tree, construct the link.
    * Flat recursively

***Construction***




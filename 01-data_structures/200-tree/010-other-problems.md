### Other Problems
| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [1530. Number of Good Leaf Nodes Pairs](https://leetcode.com/problems/number-of-good-leaf-nodes-pairs/description/) | DFS | * Count the pairs of left sub-tree, right sub-tree and current node <br> * How to calculate the distance? Utilized height | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc1530.go) | | 
| [993. Cousins in Binary Tree](https://leetcode.com/problems/cousins-in-binary-tree/description/) | DFS, BFS | | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc993.go) | | 



### BT Problems

### BT Problems - Construction

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [105. Construct Binary Tree from Preorder and Inorder Traversal](https://leetcode.com/problems/construct-binary-tree-from-preorder-and-inorder-traversal/description/) | preorder inorder | Boundary of array | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc105.go) | | 


### BT Problems - Widt & Column Related

| Problems | Solutions | Key Points | code| Comments |
| :- |:- |:- | :- | :-- |
| [662. Maximum Width of Binary Tree](https://leetcode.com/problems/maximum-width-of-binary-tree/description/) | BFS | Edged case | [code](https://github.com/brofu/leetcode/blob/main/tree/tree_lc662.go) | | 


**Binary Tree**

* LC106. Construct binary tree from preorder and inorder array
    * Recursively.
    * Key points
      * Bound of array
* LC654. Maximum Binary Tree
    * Recursively
* LC889. Construct binary tree from preorder and postorder array  
    * Recursively
    * Key Points
        * 2 situations
        * Common solution.
* LC652. Find Duplicate Subtrees
    * DFS. Post order
    * Key Points
        * Generate a `signature` for each sub tree
            * Serilize the tree or
            * generate an id for it. Pay attention to the id of `nil node`
        * Time: O(n). O(n), O(1)
        * Space: O(n)
* LC315. Count of Smaller Numbers After Self
    * Merge Sort
    * BIT
    * Complexity:
      * T:
        * Copy middle list: O(N)
        * Merge Sort: O(N*LogN) 
        * Setup Index Map: O(N)
        * Query and Update BIT: O(N*LogN)*2
      * Space
        * Middle list: O(N)
        * Index Map: O(N)
        * BIT: O(N)
* LC493. Reverse Pairs
    * Similar as LC315.
      * Reverse BIT
    * Solution 2. Only with Merge Sort
      * Key Points
        * Count first and then sort
        * count += middle-i+1
        * Complexity
          * T: 
            * Compare and Sort: 2(N*logN)
          * S:
            * O(N)
      * Why LC315 can not resolved with only Merge Sort?

* LC1664. Lowest Common Ancestor of a Binary Tree II.
  * Key Points.
    * Keep the idea of pre-order, in-order, post-order traverse...
* LC1676. Lowest Common Ancestor of a Binary Tree IV
  * Key Point.
    * Difference from LC1664??

**Complete Binary Tree**
  * Principle
    > According to Wikipedia, every level, except possibly the last, is completely filled in a complete binary tree, and all nodes in the last level are as far left as possible. It can have between 1 and 2h nodes inclusive at the last level h.

    * For any node, if it has children, then, there must be at least 1 `Perfect Binary Tree` in it's children. 
    
**Perfect Binary Tree**
  * Principle
    * Every level of the tree is full
    
**Full Binary Tree**
  * Principle
    * Every node has either has both of the 2 children or none of the 2 children.
    
**Binary Search Tree**

* Key Points
  * Use closure to reduce the complexity of passing parameters
  *
* LC230. Kth Smallest Element in a BST
    * Inorder traverse
    * Follow Up
      * Extend the BST with `NumberSumOfSubtree`
      * The operation of `Insert/Delete` elements into/from BST

* LC538. LC1038. Convert BST to Greater Tree (same as 1038)
    * DFT and right sub tree first (in order)


* LC98. Validate Binary Search Tree
  * Key Points
    * Not only the left and right child. But also all the left and right subtree
* LC700. Search in a Binary Search Tree.
* LC701. Insert into a Binary Search Tree.
* LC450. Delete Node in a BST

**Binary Indexed Tree**

![](../images/tree_bit.png?raw=true)

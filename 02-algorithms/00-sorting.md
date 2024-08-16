# Sorting

* Quick Sort
    * Quick Select
* Merge Sort

## Key Points

|Sorting Algorithm| Time Complexity | Space Complexity | Stable? | Comments |
|:--|:--|:--|:--|:--|
|Quick Sort|O(N*lgN)|O(1)|No| 1. Why not stable? A: Check the logic of finding `pivot` <br> 2. What if there is lots of duplicate elements in the input array?|
|Merge Sort|O(N*lgN)|O(N)|Yes| 1. Why is stable?|

## Thinking Patterns

### Quick Sort

* Naturally,  workflow of `Qick Sort` is very similar to the `Preorder DFS` traverse of a binary tree.
    * On each node, find the `pivot`. (The preorder logic)
    * Sort nums[low...pivot-1]. The left child logic
    * Sort nums[pivot+1...high]. The right child logic


### Merge Sort

* Naturally,  workflow of `Merge Sort` is very similar to the `Postorder DFS` traverse of a binary tree.
    * Sort nums[low...mid]. The left child logic
    * Sort nums[mid+1...high]. The right child logic
    * Merge 2 parts.  The postorder logic
    

## Problems

### Problems - Quick Sort

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/description/) | 1. Heap <br> 2. Quick Sort or Merge Sort <br> 3. Quick Select | | [heap](https://github.com/brofu/leetcode/blob/main/heap/heap_lc215.go) <br> [Quick Sort](https://github.com/brofu/leetcode/blob/main/sort/sort_lc215.go) |-| 


**Heap Sort**
  * Complexity
    * T: O(N*logN)
    * S: 
      * O(logN) Recursive
      * O(1) iterative
  * Key Points
    * In-place sorting
    * not stable. May make stable
  * About Heap
    * A complete Binary Tree
    * swim and sink are equal

**Problems**

* LC912 sort an array
  * Merge Sort. Space O(N)

* LC327 Count of Range Sum
  * Merge Sort usage.
    * handle logic and then sort
  * Similar as LC315, LC493

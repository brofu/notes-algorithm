# heap

## Key Points

## Thinking Patterns

## An Example

### Problems

### Problems - Binary Heap Problem

**Key Points**

1. Use array to present the `Binary Heap`. (完全二叉树)

**Problems**

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [215. Kth Largest Element in an Array](https://leetcode.com/problems/kth-largest-element-in-an-array/description/) | 1. Heap <br> 2. Quick Sort <br> 3. Quick Select | | [heap](https://github.com/brofu/leetcode/blob/main/heap/heap_lc215.go) | -| 


#### 295. Get the median of an ordered stream

* Key Point

  * Keep a max heap and min heap 
  * May use the go built-in heap package

      * The `up` and `down` operation is a typical `swim` and `sink` operation of a heap
      
* Principle

  * Using the heap sort. (if the stream is ordered, no need to order again)

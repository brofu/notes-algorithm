## Binary Heap

**Presentation At Code Level**

1. `Tree Node` with pointers to parent
    ```
    type HeapNode struct {
        Val int     
        Left *HeapNode
        Right *HeapNode
        Parent *HeapNode
    }
    ```

2. `Array` 

    To use `Array` to present a binary tree, the binary tree MUST be a `Complete Tree`, that's why we say that `Binary Heap` is actually a `Complete Tree`. Since we usually use the `Array` to present `Binary Heap`

    Why?

    > 1. Additional space consuming for the `pointers`
    > 2. The time complexity. For example, how to the lowest-rightest `node` in the heap? With `HeapNode`, the complexity is O(lgN), while with `Array`, we can get the data with array index, with O(1) complexity. (The `Push` and `Pop` API would be affected)
    
   

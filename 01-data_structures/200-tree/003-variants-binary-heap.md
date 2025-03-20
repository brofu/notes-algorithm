## Binary Heap

### Presentation At Code Level

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

    > * Additional space consuming for the `pointers`
    > * The time complexity. For example, how to the lowest-rightest `node` in the heap? With `HeapNode`, the complexity is O(lgN), while with `Array`, we can get the data with array index, with O(1) complexity. (The `Push` and `Pop` API would be affected)
    

### Application Scenarios 

1. `Priority Queue` 

    Key Points of `binary-heap` based priority queue

    >* `binary-heap` actually is a `Complete Tree`. Need to keep the property of `Complete Tree` during the opeartions
    >
    >   * When `Push`, append the value to the `end` of the array (to match the requirement of `Complete Tree`), and do `swim` operation.
    >
    >   * When `Pop`, return the `head` value of the array, and move the `end` of the array to the `head` location, and do `sink` operation
    >
    >* Follow the property of `max heap` or `min heap`

    [An implementation of priority queue based on binary-hap](https://github.com/brofu/leetcode/blob/main/tree/binaryheap/pq.go)

2. `Heap Sort` 

    Work flow of `heap sorting`
    * Heapify a heap. 
    * Put the heap top to the heap end and 
    * Restore the heap with array[:len(array)-2]

    [An implementation of heap sorting](https://github.com/brofu/leetcode/blob/main/tree/binaryheap/heap_sort.go)

3. `Priority Queue` V.S. `Heap Sort`
    * `Heap Sort` only use `sink` operation. Because there is actually ONLY `Pop` operation (When the heap top element found, move it to the heap end). 
    * `Priority Queue` use both `sink` and `swim` operation. Because there is `Pop` and `Push` operation. When `Push` an element into the queue, it it appended to the heap end, and `swim` to the correct location. 

       > Why not insert into the heap top, and reuse the `sink` operation? 
       >
       > Because this would cause element migration. Say that, the new one is the smallest one, then, for the `min heap`, need to move ALL the elements to the next location, with time complexity O(N)

### About Dynamic Sorting

>二叉堆就是一种能够动态排序的数据结构。所谓动态排序，就是说我们可以不断往数据结构里面添加或删除元素，数据结构会自动调整元素的位置，使得我们可以有序地从数据结构中读取元素，这是一般的排序算法做不到的。 
>
>能动态排序的常用数据结构其实只有两个，一个是优先级队列（底层用二叉堆实现），另一个是二叉搜索树。二叉搜索树的用途更广泛，优先级队列能做的事情，二叉搜索树其实都能做。但优先级队列的 API 和代码实现相较于二叉搜索树更简单，所以一般能用优先级队列解决的问题，我们没必要用二叉搜索树。



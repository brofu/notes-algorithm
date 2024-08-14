# Array & String

## Key Points

## Thinking Patterns

## An Example

## Problems

### Problems - Double Pointers

**Key Principle**

>在处理数组和链表相关问题时，双指针技巧是经常用到的，双指针技巧主要分为两类：左右指针和快慢指针。
>
>所谓左右指针，就是两个指针相向而行或者相背而行；
>
>而所谓快慢指针，就是两个指针同向而行，一快一慢。(滑动窗口是快慢指针的一个类型)
> 
>对于单链表来说，大部分技巧都属于快慢指针，单链表的六大解题套路 都涵盖了，比如链表环判断，倒数第 K 个链表节点等问题，它们都是通过一个 fast 快指针和一个 slow 慢指针配合完成任务。
>
> 在数组中并没有真正意义上的指针，但我们可以把索引当做数组中的指针，这样也可以在数组中施展双指针技巧，本文主要讲数组相关的双指针算法。

**Problems**

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [26. Remove Duplicates from Sorted Array](https://leetcode.com/problems/remove-duplicates-from-sorted-array/description/) | Double Pointers, slow + fast || [code](array_lc26.go) | |
| [83. Remove Duplicates from Sorted List](https://leetcode.com/problems/remove-duplicates-from-sorted-list/description/) | Double Pointers, slow + fast  | Edged case of `head == nil` | [code](array_lc83.go) | |
| [27. Remove Element](https://leetcode.com/problems/remove-element/description/) | Double Pointers, slow + fast  | | [code](array_lc27.go) | |
| [283. Move Zeroes](https://leetcode.com/problems/move-zeroes/description/) | Double Pointers, slow + fast |* Similar as Problem 27. Just remove the 0, and pad the index from k with 0| [code](array_lc283.go) | |
| [167. Two Sum II - Input Array Is Sorted](https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/description/) | Double Pointers, left + right, from both sides to central| | [code](array_lc167.go) | |
| [344. Reverse String](https://leetcode.com/problems/reverse-string/description/) | Double Pointers, left + right, from both sides to central | | [code](array_lc344.go) | |
| [5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/description/) | Double Pointers, left + right, from central to both sides | * 找回文串的难点在于，回文串的的长度可能是奇数也可能是偶数，解决该问题的核心是从中心向两端扩散的双指针技巧| [code](array_lc5.go) | |


**Reference**

1. https://labuladong.online/algo/essential-technique/array-two-pointers-summary-2/

### Palindromic String Problem

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/description/) | Double Pointers, left + right, from central to both sides | * 找回文串的难点在于，回文串的的长度可能是奇数也可能是偶数，解决该问题的核心是从中心向两端扩散的双指针技巧| [code](array_lc5.go) | |
| [214. Shortest Palindrome](https://leetcode.com/problems/shortest-palindrome/description/) | * Double Pointers <br> * KMP? | Refer to the code for the `Double Pointers` approach | [code](array_lc214.go) | |

### Binary Search 

**Key Points**
1. The border of [left, right], or [left, right)?


| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [704. Binary Search](https://leetcode.com/problems/binary-search/description/) | BS |* The border of [left, right] | [code](array_lc704.go) | |
| [34. Find First and Last Position of Element in Sorted Array](https://leetcode.com/problems/find-first-and-last-position-of-element-in-sorted-array/description/) | BS |* The border of [left, right]<br>* Control the left most or right most index<br>* The edged case | [code](array_lc34.go) | |
| [875. Koko Eating Bananas](https://leetcode.com/problems/koko-eating-bananas/description/) | BS |* How to abstract the problem to Binary Search | [code](array_lc875.go) | |
| [1011. Capacity To Ship Packages Within D Days](https://leetcode.com/problems/capacity-to-ship-packages-within-d-days/description/) | BS |* How to abstract the problem to Binary Search | [code](array_lc1011.go) | |

Reference:
1. https://labuladong.online/algo/essential-technique/binary-search-framework-2/
2. https://labuladong.online/algo/frequency-interview/binary-search-in-action/

### Sliding Window 

**Key Principle**

>1.我们在字符串 S 中使用双指针中的左右指针技巧，初始化 left = right = 0，把索引左闭右开区间 [left, right) 称为一个「窗口」。
2.我们先不断地增加 right 指针扩大窗口 [left, right)，直到窗口中的字符串符合要求（包含了 T 中的所有字符）。
3.此时，我们停止增加 right，转而不断增加 left 指针缩小窗口 [left, right)，直到窗口中的字符串不再符合要求（不包含 T 中的所有字符了）。同时，每次增加 left，我们都要更新一轮结果。
4.重复第 2 和第 3 步，直到 right 到达字符串 S 的尽头。
第 2 步相当于在寻找一个「可行解」，然后第 3 步在优化这个「可行解」，最终找到最优解.

Notes
1. The logic of `extend window` and `shrunk window` maybe different from problem to problem. For example, it's different for problem 76 and 159. 
2. The workflow maybe different from problem to problem also. For example, problem 395. 

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/description/) | Sliding Window | operate the supporting vars at the same time| [code](array_lc76.go) | |
| [159. Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/description/) | Sliding Window | The `extend and shrunk window` logic is different from problem 76 | [code](array_lc159.go) | |
| [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/description/) | Sliding Window | Version v2 and PV1. PV1 shows the standard workflow of `Sliding Window` clearly  | [code](array_lc3.go) | |
| [395. Longest Substring with At Least K Repeating Characters](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/description/) | Sliding Window | the workflow is different from the framework. Extend, shrunk, and the check if we have a valid result | [code](array_lc395.go) | |
| [1423. Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/description/) | Sliding Window | * Hard point is to convert the problem to sliding window scenarios. | [code](array_lc1423.go) | |
| [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/description/) | Sliding Window |*Utilize the index of character in the string | [code](array_lc424.go) | |

**Reference**
1. https://labuladong.online/algo/essential-technique/sliding-window-framework-2/

### N-Sum Problems
| Types | Problems | Key Points | Possible Solutions | Comments |
| :- | :- | :- |:- | :- | 
| nSum Problems | [259](https://leetcode.com/problems/3sum-smaller/description/) | * Double pointer <br>* Remove the duplication | [code](array_lc259.go) | | 


### LIS Problems

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [674. Longest Continuous Increasing Subsequence](https://leetcode.com/problems/longest-continuous-increasing-subsequence/description/) | | Edged case: the array ALL is increasing | [code](array_lc674.go) | |


### MergeSort Related Problems

**Key Principles**

Break down the problems into sub problems and the merge. `Divide and Conquer` 

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [315. Count of Smaller Numbers After Self](https://leetcode.com/problems/count-of-smaller-numbers-after-self/description/) |* Merge Sort<br>* Binary Indexed Tree<br> * Segment Tree | Principle why merge sort can work (R1) | [code](array_lc315.go) | |
| [493. Reverse Pairs](https://leetcode.com/problems/reverse-pairs/description/) |* Merge Sort<br>* Binary Indexed Tree<br>* Segment Tree | How to insert the logic into MergeSort | [code](array_lc493.go) | |
| [327. Count of Range Sum](https://leetcode.com/problems/count-of-range-sum/description/) |* Merge Sort<br>* Binary Indexed Tree<br>* Segment Tree | * Convert the problem to presum problem <br>* merge sort<br>* Refer to the code | [code](array_lc327.go) | |


Reference:
R1. https://labuladong.online/algo/practice-in-action/merge-sort/


### PreSum Problems

**Key Principles**

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [303. Range Sum Query - Immutable](https://leetcode.com/problems/range-sum-query-immutable/description/) | Presum | * If the `left` num is included | [code](array_lc303.go) | |
| [304. Range Sum Query 2D - Immutable](https://leetcode.com/problems/range-sum-query-2d-immutable/description/) | Presum | * if `left` is included<br> * the set calculation | [code](array_lc304.go) | |


Reference:
R1. https://labuladong.online/algo/practice-in-action/merge-sort://labuladong.online/algo/data-structure/prefix-sum/ 


### BitMask Problems

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [2506. Count Pairs Of Similar Strings](https://leetcode.com/problems/count-pairs-of-similar-strings/description/) | bitmask | should contain SAME characters | [code](array_lc2506.go) | |

### Math Related Problems

| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [1010. Pairs of Songs With Total Durations Divisible by 60](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/description/) | |*get the idea of % 60.<br>* Edged case of length = 0 or 30 | [code](array_lc1010.go) | |


### Others
| Problems | Possible Solutions | Key Points | Code | Comments |
| :- | :- | :- |:- | :- | 
| [1062. Longest Repeating Substring](https://leetcode.com/problems/longest-repeating-substring/description/) | |* 1.1 The idea of loop logic.<br> * 1.2 Stop loop in advance and edged case<br>* 2 The idea of binary search with possible length| [code](array_lc1062.go) | |

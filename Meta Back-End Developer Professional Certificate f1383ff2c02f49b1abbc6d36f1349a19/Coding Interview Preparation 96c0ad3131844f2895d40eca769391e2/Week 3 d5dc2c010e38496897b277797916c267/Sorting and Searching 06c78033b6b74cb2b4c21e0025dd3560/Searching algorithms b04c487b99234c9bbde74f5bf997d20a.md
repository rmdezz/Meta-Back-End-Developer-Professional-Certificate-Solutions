# Searching algorithms

# Introduction

In this video, you will learn about the various approaches to searching, such as linear and binary search, and the steps involved in implementing both of these approaches.

# Linear Search

The simplest search approach is a linear search. It begins at the start of the index and searches through the array until an appropriate element is found or there are no more elements to check. The best-case scenario would be O(1) and worst-case O(n) as each element would have to be checked before it's possible to say that the target element is absent.

# ****Binary Search****

A binary search will firstly check the halfway point and determines if the element is greater or smaller than the target element. If the middle element is less, then the left half of the list is discarded and the right half becomes the focus. This approach is quicker than a linear search but does require the data to be sorted before beginning the search.

The best possible outcome from this approach is that the element is found in the first go O(1). However, the worst-case scenario is less optimistic. After the first search, the list is halved. If this iteration is not successful, it is halved again. After j iterations, it is n over 2^k, or O(log n), which is considerably more efficient than a linear approach. **However, any perceived gain in time needs to be offset by the time taken to sort the list.**

![https://blog.penjee.com/wp-content/uploads/2015/04/binary-and-linear-search-animations.gif](https://blog.penjee.com/wp-content/uploads/2015/04/binary-and-linear-search-animations.gif)

# Conclusion

In this video, you learned about binary and linear search functions, the steps taken to complete these searches, and how they work. You also learned how the application of O can be used to estimate the efficiency of both. You have seen that through some clever adaptations to a standard approach, it is possible to improve performance.
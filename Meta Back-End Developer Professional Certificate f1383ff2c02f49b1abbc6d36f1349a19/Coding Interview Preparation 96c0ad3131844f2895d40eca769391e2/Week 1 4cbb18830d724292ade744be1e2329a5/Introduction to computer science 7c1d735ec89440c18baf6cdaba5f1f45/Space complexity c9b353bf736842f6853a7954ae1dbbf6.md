# Space complexity

# Introduction

When developing applications or evaluating efficiency, it is important to consider two aspects: time and space. In this video, we will focus on space complexity and its role in evaluating an algorithm's efficiency.

# ****Big-O Notation for Space Complexity****

Just like time complexity, the big-O notation is used to evaluate space complexity. The big-O notations for space complexity include O(1), O(n^2), O(log n), and others. The n in these notations refers to the size of the input and is often measured in bytes.

# ****Memory Cost in Different Languages****

The amount of memory used by an algorithm can vary based on the programming language being used. For example, in Java, an integer requires 4 bytes of memory. A blank array will consume 12 bytes for the header object and an additional 4 bytes for padding.

# ****Auxiliary and Input Space****

When evaluating space complexity, it is important to consider both auxiliary and input space. Auxiliary space is the space required to hold all data needed for the solution. It refers to the temporary space needed to compute the solution. Input space refers to the space required to add data to the system being evaluated.

# ****Memory Usage Considerations****

When designing an algorithm, it is important to be mindful of memory usage. Common actions that increase memory usage include assigning variables, creating new data structures, function calling and allocation, and copying arrays or complex data structures. Writing functions that use complex structures when simpler structures would suffice can also incur a penalty.

# Summary

In computer science, time and space complexity are two important factors to consider when evaluating the efficiency of algorithms. Time complexity refers to the amount of time an algorithm takes to complete a task, while space complexity refers to the amount of memory an algorithm uses while running.

## Example

Let's take a look at an example to see the difference between time and space complexity. Consider a simple sorting algorithm that sorts an array of numbers. 

The time complexity of this algorithm would depend on how fast it can sort the array, for example, if it uses bubble sort, the time complexity would be O(n^2), where n is the number of elements in the array. 

On the other hand, the space complexity of this algorithm would depend on the amount of memory it uses, for example, if the algorithm sorts the array in place, it would have a space complexity of O(1), as it would only use a constant amount of memory regardless of the size of the array.

When an algorithm sorts an array "in place", it means that the algorithm sorts the elements of the array within the same array, without using any additional memory space to store the sorted elements. In other words, it sorts the elements in the original array, rather than copying the elements to a new array and sorting them there. The space complexity of an in-place sorting algorithm is O(1), because it only requires a constant amount of extra memory space, regardless of the size of the input array.

On the other hand, if an algorithm sorts the array not in place, it would require additional memory space proportional to the size of the input array, for storing the sorted elements. In this case, the space complexity of the algorithm would be O(n), where n is the size of the input array. This is because the algorithm needs to allocate memory space for a new array that is the same size as the input array, in order to store the sorted elements.

# ****Conclusion****

In this video, we learned about space complexity and its role in evaluating an algorithm's efficiency. We also discussed the big-O notation for space complexity and memory cost in different programming languages. Additionally, we touched on the importance of considering auxiliary and input space and memory usage considerations when designing an algorithm.
# Time complexity

# Introduction

In computer science, evaluating the efficiency of applications or algorithms involves considering two aspects: time and space. In this video, we'll focus on evaluating time efficiency, also known as time complexity.

# The Big-O Notation

Big-O notation is a metric for determining an algorithm's efficiency by estimating how long it will take to run on different sets of inputs. The following are some of the Big-O notations you may encounter:

## O(1)

This means the algorithm takes a constant time, or one single computation, no matter what the input is. An example of this would be printing the first item in an array.

## O(log n)

This is a logarithmic search, meaning the time it takes to run the algorithm increases only slightly as the input increases. A binary search is an example of an O(log n) algorithm.

## O(n)

This is a linear time complexity, meaning the time it takes to run the algorithm is directly proportional to the size of the input. An example of this would be searching an array for a specific value.

## O(n^2)

This is a quadratic time complexity, meaning the time it takes to run the algorithm is proportional to the square of the size of the input. An example of this would be checking every combination of elements in a two-dimensional array.

# Graphical Representation of Time Complexity

![Screenshot 2023-02-11 at 12.08.45 PM.png](Time%20complexity%207601e44b7df347b1856c6ef89176cd5b/Screenshot_2023-02-11_at_12.08.45_PM.png)

The x-axis of the graph represents the number of inputs and the y-axis represents the time taken. As the number of inputs increases, the gradient of the line for all cases except O(1) will also increase. The best time complexity to aim for is O(1), followed by O(log n), then O(n), and finally, O(n^2).

# Best case, worst case, and average case

When evaluating an algorithm, it's important to consider the best case, worst case, and average case scenarios. For example, in a search algorithm, the best case would be finding the desired value as the first element, the worst case would be not finding it at all, and the average case would be finding it somewhere in the middle.

![Screenshot 2023-02-11 at 12.09.52 PM.png](Time%20complexity%207601e44b7df347b1856c6ef89176cd5b/Screenshot_2023-02-11_at_12.09.52_PM.png)

# Conclusion

In this video, we introduced the concept of time complexity and how to evaluate the efficiency of algorithms using Big-O notation. When developing solutions to problems, it's important to consider the number of computations your solution employs and whether there's a more efficient way. Time complexity is just one aspect of evaluating efficiency, and in the next video, we'll focus on space complexity.
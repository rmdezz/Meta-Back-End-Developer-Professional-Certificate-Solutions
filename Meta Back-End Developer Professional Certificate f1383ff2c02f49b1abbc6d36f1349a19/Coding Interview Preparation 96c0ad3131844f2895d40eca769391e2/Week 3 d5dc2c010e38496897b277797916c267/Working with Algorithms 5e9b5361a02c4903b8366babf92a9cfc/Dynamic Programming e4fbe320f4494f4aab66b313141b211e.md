# Dynamic Programming

In this video, you will learn about the concepts of memorization and dynamic programming. These techniques are used to solve problems by breaking them into smaller sub-problems and then storing the solutions for future use, reducing the computation time.

# **Quick Recap**

- Divide and conquer: Breaking down a large problem into smaller sub-problems and solving them.
- Recursion: A technique where a function calls itself to solve a problem, avoiding loops.

# ****What is Dynamic Programming?****

Dynamic programming is an extension of the divide and conquer and recursion techniques, with the added step of keeping track of the results generated from running the sub-problems. The solutions are stored in a data structure for later use, avoiding the need to re-compute the same sub-problems multiple times. This approach is called memorization.

# **What are the steps of Dynamic Programming?**

1. Determine the objective function: This is the description of what the optimal outcome is to be.
2. Break the problem into smaller steps: This can be done through the use of recursive functions.
3. Use memorization: Store the results generated from running the sub-problems, avoiding the need to re-compute them.

# When to use Dynamic Programming?

Dynamic programming is commonly used for combination and optimization problems, such as the Fibonacci sequence and the knapsack problem. In the knapsack problem, you are given a list of items with different weights and values, and you have to find the best combination of items to fit in a knapsack with a certain weight capacity. By using dynamic programming, you can save the computations used to find the solution for a given weight, avoiding the need to re-compute them when the weight changes.

# ****Example****

Consider the problem of finding the number of combinations for a binary lock with six digits. Using the exponentiation method, we can calculate that the number of combinations is 2^6 = 64. To optimize this calculation, we can use dynamic programming by breaking down the problem into smaller steps and storing the solutions for later use. For example, we can calculate 2^3 and use that solution twice, reducing the overall computation required.

# ****Conclusion****

Dynamic programming is an approach that optimizes solutions to problems by breaking them into smaller sub-problems, storing the solutions for future use, and avoiding the need to re-compute the same sub-problems multiple times. It combines the principles of memorization and overlapping sub-problems to identify when an objective function can be achieved quickly, optimizing the computation steps required.
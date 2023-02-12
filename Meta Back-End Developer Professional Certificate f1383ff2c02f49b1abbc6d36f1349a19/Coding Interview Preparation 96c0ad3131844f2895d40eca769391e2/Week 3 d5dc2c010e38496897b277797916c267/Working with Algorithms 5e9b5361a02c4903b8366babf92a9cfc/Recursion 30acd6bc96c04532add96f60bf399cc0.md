# Recursion

In this video, you'll learn about recursion, an alternative approach to solving problems than using loops. Recursion is a technique where a function calls itself with a smaller instance of a problem until a certain exit condition is met.

# ****Requirements for Recursive Solutions****

To implement a recursive solution, there are three requirements:

- Base case: A termination point for the function, where it stops calling itself.
- Diminishing structure: The input value must be reduced each time the function is called.
- Recursive call: The function must call itself with the reduced structure.

# **Example of Recursion**

Consider finding the exponent of a number. The base case is if the exponent is 0. The diminishing structure is reducing the input value by multiplying it by the exponent. The recursive call is the function calling itself with the reduced input.

```python
def exponent(x, n):
    if n == 0:
        return 1
    else:
        return x * exponent(x, n-1)
```

The base case ensures that the function will not continue to call itself and eventually ends. In this instance, the base case is if **`n`** equals 0. In this instance, the program will terminate and return 1.

The second part of the function is the diminishing structure. If a termination point has not been reached, call the function again with a reduced structure. In this instance, the goal is to multiply **`x`** by **`n`** to find the total number of potential states that could exist for the binary number. Reducing the input value is as important as establishing a base case. This way, the function will eventually reach the base case and cease to call itself.

The third component of a recursive function is to include a call to itself. This happens on the last line of the code, where the exponent is accepting the diminished structure. The structure can be said to be diminished because the size has been reduced from one call to another. Each time the function is called, a new instance is created on the call stack.

# **Use of Recursion**

Recursion can be used when solving problems like binary search, where the input list and target value are passed to the function, and it calls itself until the target endpoint is reached. Recursion can lead to more readable code and is often used as part of a divide and conquer solution, breaking the problem into smaller parts and solving those.

# **Benefits of Recursion**

- Readability: Recursive solutions can reduce the amount of code required to solve a problem and can be easier to read and understand.
- Divide and conquer approach: Recursion embodies the divide and conquer approach, breaking the problem into its smallest components and solving those.

# Note

Keep in mind that recursion can add some computation overhead to a problem.
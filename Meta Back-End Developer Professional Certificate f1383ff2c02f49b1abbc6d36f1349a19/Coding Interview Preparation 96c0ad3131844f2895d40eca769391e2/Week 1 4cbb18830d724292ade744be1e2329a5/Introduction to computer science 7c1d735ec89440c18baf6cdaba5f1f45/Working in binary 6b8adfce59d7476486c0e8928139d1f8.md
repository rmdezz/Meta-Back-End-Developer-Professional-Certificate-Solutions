# Working in binary

# ****Introduction****

It is common knowledge that computers think in zeroes and ones. But, how this works in practice is a little more complex than one might initially think. You previously explored how computers utilize binary data to store and process information. In this reading, you will learn more about binary, including how to work with Boolean logic, truth tables and gates.

You may think that using only two inputs is restrictive. However, it is extraordinarily versatile and offers a broad range of options if combined with Boolean algebra and circuits.

# ****Boolean logic****

A Boolean function maps two inputs to a value. These inputs are limited to two states. These states can be considered: **on/off**, **true/false** or **1/0**. To define a Boolean function, you only need to specify the output from its inclusion. Here is an example of 4 functions:

![Untitled](Working%20in%20binary%206b8adfce59d7476486c0e8928139d1f8/Untitled.png)

**NOT** takes in one value **x** and resolves it to either a **0** or **1**. 

**OR** takes two arguments **(x, y)** to generate an output of **1**. Only one of the **x** or **y** values must be **1**. If both values are **0**, the output is **0**. 

**AND** requires both inputs to be **1** before it can generate a **1**. 

Finally, **XOR** will take any two values and determine if they are the same; if so, the output is **1**. In all other cases, the result is **0**.

![Untitled](Working%20in%20binary%206b8adfce59d7476486c0e8928139d1f8/Untitled%201.png)

The same concepts can be represented computationally. In this table, the Boolean expressions are on the left, and their computational symbols are on the right. Most commonly, they are combined with conditional statements or iterators. So, you could expect code that resembles the following code snippet:

![Untitled](Working%20in%20binary%206b8adfce59d7476486c0e8928139d1f8/Untitled%202.png)

In the above code, a Boolean has been set to false. A **do/while** loop then continually executes the code found within the do until the value for **x** switches to **true**. Generally, you would be looking for a specific outcome, and using Boolean logic enables you to keep looking until the result becomes **true**. Notice how the **NOT** function is applied in the **while** loop to test if another iteration should exist.

# Truth tables

Given the finite number of outputs to the Boolean functions, it is possible to plot all permutations to a table.

![Untitled](Working%20in%20binary%206b8adfce59d7476486c0e8928139d1f8/Untitled%203.png)

This image demonstrates all the permutations for each of the Boolean functions. The **X** and **Y** columns denote whether it receives a **0** or **1**, and the **XY** indicates the eventual outcome. The **NOT** function only has one output and input, so the table is only **2 x 2**. In comparison, the other three examples all take two inputs and generate a single result.

# Gates

The fundamental building block for digital logic circuits is the gate. The logical functions are then implemented through their interconnectedness. A gate is an electronic circuit that generates a Boolean output from its inputs.

![Untitled](Working%20in%20binary%206b8adfce59d7476486c0e8928139d1f8/Untitled%204.png)

In the above image, the four basic Boolean functions are illustrated. Graphical Symbol is how these gates are represented on diagrams. You will often encounter circuit diagrams that host a series of interconnected gates. The Algebraic function demonstrates how these gates are described when written as formulae.

Finally, the truth tables outline the outcomes from a given input to the gate. On a primitive level, each input denoted by **A** and **B** represents a current that can be passed through the circuit. These inputs may be connected to a switch, or a button, that can be activated causing a **0** or **1** to be transmitted. The expression of this Boolean logic builds when circuit gates are combined to form complex circuits. The final output **Q** is determined from the machinations performed on the inputs **A**, **B**, and **C**.

![Untitled](Working%20in%20binary%206b8adfce59d7476486c0e8928139d1f8/Untitled%205.png)

# Conclusion

This reading demonstrates how a simple **0** and **1** can be combined and amplified through Boolean logic, truth tables and logic gates to generate more complex outputs. You have learned more about binary, including how to work with boolean logic, truth tables and gates.
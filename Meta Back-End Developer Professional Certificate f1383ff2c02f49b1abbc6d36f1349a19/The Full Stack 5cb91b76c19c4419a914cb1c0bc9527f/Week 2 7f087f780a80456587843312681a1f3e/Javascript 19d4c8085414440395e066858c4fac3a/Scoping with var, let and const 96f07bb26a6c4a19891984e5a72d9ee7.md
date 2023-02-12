# Scoping with var, let and const

Scoping in JavaScript determines which parts of the code are accessible by different parts of the program. There are 3 types of scopes:

- Global scope: The code outside of functions.
- Local scope: The code inside of a function. A variable declared in local scope is only accessible in the function where it is declared.
- Block scope: A variable declared in a block of code is only accessible inside that block. The block scope is built when you declare variables using **`let`** or **`const`**.

## **Declaring Variables in JavaScript**

Before ES6, the only way to declare a variable in JavaScript was to use the **`var`** keyword. Variables declared with **`var`** are:

- Can be used in code even before they are declared
- Can be redeclared
- Scoped to a function if declared inside, else they are scoped globally

With ES6, it is recommended to use the **`let`** or **`const`** keywords to declare variables. **`let`** is used if the value might change in the future, and **`const`** is used if the value will never change.

## ****Examples****

Declaring a variable named **`user`** with **`var`** in ES5:

```jsx
var user = "Miranda"
```

Declaring a variable named **`user`** with **`let`** in ES6:

```jsx
let user = "Miranda"
```

Declaring a constant named **`user`** with **`const`** in ES6:

```jsx
const user = "Miranda"
```

# Conclusion

In this video, you learned about the different scoping concepts in JavaScript and the difference between **`var`**, **`let`**, and **`const`** in declaring variables.
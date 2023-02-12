# Data Types

# Introduction

Imagine you're moving to a new place and need to pack your belongings efficiently. A good start would be to sort items into boxes and label them so you know what's in each box. Similarly, programming requires using the right data type to store information effectively. 

**In JavaScript, there are 7 primitive data types:** 

1. string,
2. number,
3. Boolean,
4. null,
5. undefined,
6. BigInt,
7. and symbol. 

In this video, you'll learn about these data types and their specific use cases.

# String and Number Data Types

Let's consider an example of building an E-commerce app for selling guitars. When a user views the page for the most popular model, you want them to see the name of the guitar, its description, and its price. 

To store this information effectively, you'll use the appropriate data type. In JavaScript, text values are stored as the string data type and numerical values as the number data type.

```jsx
// Store the name and description as strings
var name = "The Best Guitar Around";
var description = "The best guitar you'll ever play";

// Store the price as a number
var price = 375;
```

# Boolean Data Type

The Boolean data type has only two values: true and false. It's useful for making decisions in your code.

```jsx
// Example usage of the Boolean data type
var isInStock = true;

if (isInStock) {
  console.log("Guitar is in stock");
} else {
  console.log("Guitar is out of stock");
}
```

```jsx
**// Render Output:**
// Guitar is in stock
```

# ****Null and Undefined Data Types****

Sometimes it's necessary to know when a variable doesn't contain a value. JavaScript has two data types to express this: the null and undefined data types. 

- The null data type only has the value null and represents the absence of value.
- The undefined data type can only hold the value undefined and usually refers to a variable that hasn't been assigned a value.

```jsx
// Example usage of the null data type
var guitarColor = null;
console.log(guitarColor);

**// Render Output:**
// null

// Example usage of the undefined data type
var guitarMaterial;
console.log(guitarMaterial);

**// Render Output:**
// undefined
```

# BigInt Data Type

JavaScript's capabilities have evolved over time and version ES6 introduced the BigInt data type to help with more complex tasks. The BigInt data type is like an extra large box that can accommodate a greater range of numbers than the number data type.

```jsx
// Example usage of the BigInt data type
var guitarSerialNumber = BigInt(9007199254740992);
console.log(guitarSerialNumber);

**// Render Output:**
// 9007199254740992n
```

# ****Symbol Data Type****

The symbol data type can be used as a unique identifier. Consider it as having multiple boxes with the same label and using different serial numbers to avoid mixing them up.

```jsx
// Example usage of the Symbol data type
var guitarIdentifier = Symbol("Guitar1");
var ampIdentifier = Symbol("Amp1");
console.log(guitarIdentifier === ampIdentifier);

**// Render Output:**
// false
```

# Conclusion

In this video, you learned about the 7 primitive data types.
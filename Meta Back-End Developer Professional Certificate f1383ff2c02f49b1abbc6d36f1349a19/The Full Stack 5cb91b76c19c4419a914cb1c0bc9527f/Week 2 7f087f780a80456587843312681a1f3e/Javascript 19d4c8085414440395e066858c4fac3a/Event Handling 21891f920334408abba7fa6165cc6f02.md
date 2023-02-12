# Event Handling

# Introduction

- User triggered events are actions performed by the user on a webpage, such as clicking a button or tapping a like icon.
- JavaScript can listen for these events and run code when they occur.
- An example of a user triggered event is clicking an "Add to Cart" button, which can trigger code to update a shopping cart icon with the number of items in the cart.

# Listening for Events

- In JavaScript, the function that handles captured events is called the event handler.
- There are two ways to listen for events in JavaScript:
    1. Using the addEventListener method
    2. Using HTML event attributes

# ****Using the addEventListener Method****

**Example**

```jsx
const target = document.querySelector('body');

function handleClick() {
  console.log('clicked the body');
}

target.addEventListener('click', handleClick);
```

![Screenshot 2023-02-07 at 12.20.57 AM.png](Event%20Handling%2021891f920334408abba7fa6165cc6f02/Screenshot_2023-02-07_at_12.20.57_AM.png)

# ****Using HTML Event Attributes****

**Example:**

```jsx
function handleClick2() {
  console.log('clicked the heading');
}

<h1 onclick="handleClick2()">Heading</h1>
```

![Screenshot 2023-02-07 at 12.21.34 AM.png](Event%20Handling%2021891f920334408abba7fa6165cc6f02/Screenshot_2023-02-07_at_12.21.34_AM.png)

# Conclusion

You have learned how to write an event listener using both the addEventListener method and by writing a function directly as an HTML event attribute.
# Programming in JavaScript

# Introduction

JavaScript is a widely used programming language that can be found in many different scenarios such as the browser, server, mobile apps, and the Internet of Things. It is everywhere, making it a versatile language with many different use cases.

# Use cases of JavaScript

- **In the Browser:** JavaScript is used in the browser to add various behaviors and interactivity, such as adding an item to a shopping cart when clicking a button.
- **On the Server:** JavaScript can be used on the server to power up websites, communicate with databases, and provide native fields to web apps.
- **Mobile Apps:** JavaScript can be used to build mobile apps using technologies like React Native.
- **Internet of Things:** JavaScript can be used to program devices known as the Internet of Things.

# Compatibility Issues with JavaScript

In the early 2000s, different companies built Internet browsers and they had different behaviors and discrepancies between them. This resulted in developers sometimes having to write separate JavaScript code for different browsers, leading to a frustrating experience for end-users.

# Solutions to Compatibility Issues

Out of frustration, several projects emerged trying to solve the compatibility problem, including the popular library, jQuery. With jQuery, developers only needed to import the library and write code using its features, making it work across all browsers.

However, as the web and the way we code continued to evolve, new problems appeared, and new solutions were needed. One such solution was **`React`**, which solved many of the issues associated with creating, updating, and maintaining complex websites. Other technologies, such as Knockout, Backbone, Angular, Ember, Vue, and Alpine, have also emerged.

# Legacy Code

With millions of websites containing JavaScript code from different versions and libraries, there is a lot of old code, known as legacy code. While you may not use jQuery to build a modern website today, you may still come across it in an actively running project.

# Learning JavaScript

While beginners may feel overwhelmed with the different technologies associated with JavaScript, it is not necessary to learn or master all of them. To be a well-rounded developer, it is essential to learn and master the basics of plain JavaScript without the frameworks. **Once you have this foundation, it will be easier to learn a framework built on top of JavaScript, such as React.**

# Example of JavaScript

```css
// Simple JavaScript code to display an alert message

alert("Hello World!");

// Output: an alert box with the message "Hello World!"
```

# Example of JavaScript with React

```css
// Simple React code to display "Hello World!"

import React from "react";

function App() {
  return <h1>Hello World!</h1>;
}

export default App;

// Output: the page will display "Hello World!" using an H1 header.
```
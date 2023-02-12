# JavaScript DOM manipulation

- The DOM (Document Object Model) is like a remote control for web pages.
- It allows developers to manipulate and update webpages.
- The DOM is saved in the browser's memory in the form of a JavaScript object with nested objects for different parts of the page.
- Developers can interact with the DOM using the browser's DevTools (Elements tab) or JavaScript.
- The entire DOM object is saved inside the document variable and is accessible via the console.

# Creating a Heading Element

- To create a heading element using the DOM, you need to update the document object.
- You can do this by using the createElement method and passing the tag name of the HTML element as a string.

For example:

```jsx
const h2 = document.createElement('h2');
```

- You can then add some text to the heading element using the innerText method:

```jsx
h2.innerText = "This is an h2 heading";
```

- You can also add HTML attributes to the heading element using the setAttribute method:

```jsx
h2.setAttribute('id', 'sub-heading'); 
h2.setAttribute('class', 'secondary');
```

- Finally, you need to append the heading element to the DOM using the appendChild method:

```jsx
document.body.appendChild(h2);
```

Example Output:

The heading element will be displayed on the webpage:

```jsx
<h2 id="sub-heading" class="secondary">This is an h2 heading</h2>
```

![Screenshot 2023-02-07 at 12.07.41 AM.png](JavaScript%20DOM%20manipulation%2065ab1683ad9243b69d52916e29a95ac5/Screenshot_2023-02-07_at_12.07.41_AM.png)

# Summary

- In this lesson, you learned about the basics of DOM manipulation and how to use common DOM manipulation methods.
- You learned how to create a heading element, add text and HTML attributes to it, and append it to the DOM.
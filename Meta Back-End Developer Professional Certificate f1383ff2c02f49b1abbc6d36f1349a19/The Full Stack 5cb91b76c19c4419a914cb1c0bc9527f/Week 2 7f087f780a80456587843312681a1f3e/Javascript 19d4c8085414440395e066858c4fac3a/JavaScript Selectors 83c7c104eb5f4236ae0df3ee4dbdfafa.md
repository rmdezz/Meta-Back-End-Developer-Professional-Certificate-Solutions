# JavaScript Selectors

JavaScript provides several methods to quickly locate specific elements in an HTML document stored in the browser's memory, also known as the Document Object Model (DOM). 

These selectors allow you to manipulate the elements in real-time, giving you the power to change the color of text, display pop-up messages, and much more.

## ****querySelector Method****

The **`querySelector`** method is used to access the first matching element in the document. For example, to access the first **`p`** element on the page:

```jsx
document.querySelector('p')
```

The output:

```jsx
<p>Paragraph 1</p>
```

## querySelectorAll Method

The **`querySelectorAll`** method is used to access all the matching elements in the document. For example, to access all the **`p`** elements on the page:

```jsx
document.querySelectorAll('p')
```

The output:

```jsx
NodeList(2) [p, p]
```

## getElementById Method

The **`getElementById`** method is used to access an element in the document that matches a specified ID attribute. For example, to access an element with the ID attribute value of **`heading`**:

```jsx
document.getElementById('heading')
```

The output:

```jsx
<h1 id="heading">Heading</h1>
```

## ****getElementsByClassName Method****

The **`getElementsByClassName`** method is used to access all the elements in the document that match a specified class name. For example, to access all the elements with the class name of **`txt`**:

```jsx
document.getElementsByClassName('txt')
```

The output:

```jsx
HTMLCollection(2) [p, p]
```

## Note

**Note:** It's important to note that the word **`element`** is singular for **`ID`** and plural for class name. If the desired element cannot be found, the method will return **`null`** for **`ID`** and an empty collection represented by square brackets for class names.

# Conclusion

With these selectors, you can quickly find specific elements in your HTML document and manipulate them using JavaScript.
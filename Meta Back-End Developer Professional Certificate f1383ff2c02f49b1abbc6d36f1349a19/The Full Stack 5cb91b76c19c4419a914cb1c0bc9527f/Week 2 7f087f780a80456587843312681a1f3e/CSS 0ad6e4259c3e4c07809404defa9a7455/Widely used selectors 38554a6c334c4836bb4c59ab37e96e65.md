# Widely used selectors

In this video, we will be revisiting the CSS selectors that we have covered before and learning about additional commonly used CSS selectors. Let's start by quickly reviewing the selectors you are already familiar with:

# Element or Type Selectors

This selector allows developers to select HTML elements based on their element type. For example, to select all **`p`** elements, the CSS rule would be:

```css
p {
    color: blue;
}
```

**Output:**

```html
<p> This is a blue paragraph. </p>
```

# ID Selectors

ID selectors use the **`id`** attribute of HTML elements. Since the **`id`** is unique within a web page, it allows the developer to select a specific element for styling. For example, to select an element with **`id`** equal to "header", the CSS rule would be:

```css
#header {
    background-color: green;
}
```

**Output:**

```html
<div id="header"> This is a green header. </div>
```

# Class Selectors

Class selectors allow you to select elements based on the **`class`** attribute applied to them. With class selectors, you can apply rules to all elements with the specified class name. For example, to select elements with **`class`** equal to "highlight", the CSS rule would be:

```css
.highlight {
    font-weight: bold;
}
```

**Output**:

```css
<p class="highlight"> This is a bold paragraph. </p>
```

# Additional CSS Selectors

Let's now explore a few additional widely used CSS selectors:

## Attribute Selectors

Attribute selectors **match the attribute and value for a given element.** For example, to select all **`a`** elements with **`href`** equal to "**[https://www.example.com](https://www.example.com/)**", the CSS rule would be:

```css
a[href="https://www.example.com"] {
    color: red;
}
```

**Output:**

```css
<a href="https://www.example.com"> This is a red link. </a>
```

## nth-of-type and nth-child selectors

These selectors target the nth-child or nth-type of a specified parent element. For example, to select the second **`li`** element within a **`ul`**, the CSS rule would be:

```css
ul li:nth-child(2) {
    background-color: yellow;
}
```

**HTML:**

```css
<ul>
    <li> Item 1. </li>
    <li> Item 2. </li>
    <li> Item 3. </li>
</ul>
```

**Output:**

```css
Item 1. 
Item 2. (in yellow background)
Item 3.
```

## Start Selector

This selector is used for selecting all the elements of a web page. For example, to set the default margin for all elements, the CSS rule would be:

```css
* {
    margin: 10px;
}
```

## Group Selector

- Instead of using element selectors for each type of element, you can group multiple selectors together and apply the same styling to all elements in the group.
- For example, to apply the same styling to both heading 1 and paragraph elements, you can use:

```css
h1, p {
  font-size: 20px;
  color: blue;
}
```

**Output:**

```css
<h1>Hello World</h1>
<p>This is a paragraph.</p>

Hello World
This is a paragraph.
```

This will change the font size and color of both the heading 1 and paragraph elements to 20px and blue, respectively.

Group selectors can save you time and they're also known as "selector stacking".

# Conclusion

- In this video, you reviewed the CSS selectors that you are familiar with and learned about additional commonly used CSS selectors.
- Understanding how to use CSS selectors is important because it allows you to be more specific when styling your web pages.

In the rest of the lesson, you'll be introduced to more advanced selectors. At first, they might seem more complex than the ones covered in this video, but with a bit of practice, they will become part of your everyday web styling toolkit.
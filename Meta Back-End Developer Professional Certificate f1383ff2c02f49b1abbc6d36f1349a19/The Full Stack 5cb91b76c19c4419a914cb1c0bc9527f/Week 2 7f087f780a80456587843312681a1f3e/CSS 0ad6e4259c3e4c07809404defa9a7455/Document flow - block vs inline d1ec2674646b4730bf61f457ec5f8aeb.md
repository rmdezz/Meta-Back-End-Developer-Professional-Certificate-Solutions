# Document flow - block vs. inline

In CSS, the default way of calculating the position of HTML elements on the screen is called document flow. Nearly all HTML elements are organized into one of two categories: block and inline elements.

# Block elements

Block level elements occupy the full width of their parent element and create a new line before and after. This means that multiple block level elements stack on top of each other like a stack of boxes. Examples of block level elements include **`div`**, **`form`**, and **`heading`** tags.

```css
+-----------------------------------------------+
|                                               |
|  +-------------------------------------------+
|  |                                           |
|  |  Block level element                      |
|  |                                           |
|  +-------------------------------------------+
|                                               |
|  +-------------------------------------------+
|  |                                           |
|  |  Another block level element              |
|  |                                           |
|  +-------------------------------------------+
|                                               |
+-----------------------------------------------+
```

# Inline elements

Inline elements only occupy the width and height of their content and do not create a new line. This means that multiple inline elements form a row of elements. Examples of inline elements include **`anchor`**, **`image`**, **`input`**, **`label`**, **`bold`**, **`italics`**, **`emphasis`**, and **`span`** tags.

```css
+-----------------------------------------------+
|                                               |
|  Inline element   Inline element   Inline     |
|                                               |
+-----------------------------------------------+
```

# Document Flow Example

Let's see an example of how you can change elements from block level to inline and vice versa using the **`display`** CSS property.

Consider the following HTML file:

```css
<div>
  <span>Block level element 1</span>
  <span>Block level element 2</span>
  <span>Block level element 3</span>
</div>
```

This would render as:

```css
+-----------------------------------------------+
|                                               |
|  Block level element 1   Block level element 2|
|  Block level element 3                        |
|                                               |
+-----------------------------------------------+
```

Now, if we change the second element from a **`span`** to a **`div`**:

```css
<div>
  <span>Block level element 1</span>
  <div id ="middle">Block level element 2</div>
  <span>Block level element 3</span>
</div>
```

This would render as:

```css
+-----------------------------------------------+
|                                               |
|  Block level element 1                        |
|                                               |
|  +-------------------------------------------+
|  |                                           |
|  |  Block level element 2                    |
|  |                                           |
|  +-------------------------------------------+
|                                               |
|  Block level element 3                        |
|                                               |
+-----------------------------------------------+
```

And if we use the **`display`** property in CSS to change the second element back to an inline element:

```css
#middle {
    display: inline;
  }
```

And the output in the browser would look like this:

```css
+-----------------------------------------------+
|                                               |
|  Block level element 1   Block level element 2|
|  Block level element 3                        |
|                                               |
+-----------------------------------------------+
```

To change the middle element back to a block element:

```css
#middle {
    display: block;
}
```

Output:

```css
+-----------------------------------------------+
|                                               |
|  Block level element 1                        |
|                                               |
|  +-------------------------------------------+
|  |                                           |
|  |  Block level element 2                    |
|  |                                           |
|  +-------------------------------------------+
|                                               |
|  Block level element 3                        |
|                                               |
+-----------------------------------------------+
```
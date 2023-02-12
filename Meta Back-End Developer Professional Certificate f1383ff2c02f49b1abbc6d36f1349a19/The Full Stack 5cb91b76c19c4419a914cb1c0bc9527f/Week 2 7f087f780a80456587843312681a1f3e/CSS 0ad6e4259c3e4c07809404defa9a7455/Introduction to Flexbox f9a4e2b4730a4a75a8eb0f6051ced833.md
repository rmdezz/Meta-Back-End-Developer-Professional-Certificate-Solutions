# Introduction to Flexbox

At this point, you should have a good understanding of different layout and grid structures, and be ready to start using Flexbox. In the next few minutes, we'll explore the three most common uses of Flexbox in CSS. 

Flexbox is best suited for simple layouts or designing simple elements on a page, and we'll explore a few common design elements to show how Flexbox can be used for binding elements together or creating an easy layout.

# Common Uses of Flexbox

1. Search Bars
2. Navigation Bars
3. Image Galleries

# Example 1: Search Bars

Let's start with a search bar, one of the most common uses of Flexbox. In this example, we'll create a search bar that ties together the search icon, search input area, and submit button.

## HTML Code

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <link rel="stylesheet" href = "flexbox_search.css">
    <title>Document</title>
</head>
<body>
    <div class="contaner">
        <img class="icon" src="search.svg" alt="Sample image" style="width: 32px; height: 24px;">
        <input class="searchBox" type="search" name="search" placeholder="Enter text here">
        <input type="submit" value="search" class="searchButton">
    </div>
</body>
</html>
```

### Explanation

```css
**<div class="container">**

	class="container": This is a CSS class selector that is used to apply styles to a specific HTML element. In this case, the styles for the "container" class will be used to format the div element and its contents.
```

```css
**<img class="icon" src="search.svg" alt="Sample image" style="width: 32px; height: 24px;">**

class="icon": This is a CSS class selector that is used to apply styles to a specific HTML element. In this case, the styles for the "icon" class will be used to format the image element.

src="search.svg": This attribute specifies the source file for the image. The "search.svg" file is the path to the image file that will be displayed on the page.

alt="Sample image": This attribute provides a text description of the image for accessibility purposes. Screen readers will use this text to describe the image to users who are visually impaired.

style="width: 32px; height: 24px;": This is an inline CSS style that is used to set the width and height of the image. The values of "32px" and "24px" specify the dimensions of the image.
```

```css
**<input class="searchBox" type="search" name="search" placeholder="Enter text here">**

class="searchBox": This is a CSS class selector that is used to apply styles to a specific HTML element. In this case, the styles for the "searchBox" class will be used to format the input element.

type="search": This attribute specifies the type of input that the element represents. In this case, the input type is "search", which means that the input element is a search box.

name="search": This attribute provides a name for the input element. This name is used to identify the input when the form data is submitted to the server.

placeholder="Enter text here": This attribute provides a text description of the input element that is displayed in the input field before the user enters any text. This text acts as a placeholder for the input and provides a hint to the user about what they should enter in the field.
```

```css
**<input type="submit" value="search" class="searchButton">**

type="submit": This attribute specifies the type of input that the element represents. In this case, the input type is "submit", which means that the input element is a submit button.

value="search": This attribute provides the text that will be displayed on the submit button. In this case, the text is "search".

class="searchButton": This is a CSS class selector that is used to apply styles to a specific HTML element. In this case, the styles for the "searchButton" class will be used to format the submit button element.
```

### Is the “type” attribute necessary?

The **`type`** attribute is necessary in this example because it specifies the type of the input element. The **`input`** element can have different types, such as text, password, checkbox, radio, etc. The type attribute determines the behavior and appearance of the input element in a form.

There are several conventions of default accepted values that the **`type`** attribute can accept. Some of the most commonly used input types are:

- text: The default type for an **`input`** element. It creates a single-line text input field.
- password: Creates a password input field where the entered text is masked.
- checkbox: Creates a checkbox that the user can toggle on or off.
- radio: Creates a radio button that allows the user to select one option from a group of options.
- submit: Creates a submit button that submits the form data to the server.
- reset: Creates a reset button that resets the form data to its original values.
- button: Creates a button that can be used to trigger JavaScript events.

These are just a few of the accepted values for the **`type`** attribute. The full list of accepted values can be found in the HTML specification.

### What happens if I don’t use the type attribute?

If the type attribute is not used in the input element, **the default type of "text" will be applied.** This means that the input will function as a text input field and the user will be able to type any text into it.

However, in this case, the input element is used to create a search box, so it is recommended to specify the type as "search". This way, the browser will know that it should provide a search input field with specific behavior, such as a clear button to clear the text and a submit button to start the search.
**Clear button (the x mark):**

![Screenshot 2023-02-05 at 3.30.21 PM.png](Introduction%20to%20Flexbox%20f9a4e2b4730a4a75a8eb0f6051ced833/Screenshot_2023-02-05_at_3.30.21_PM.png)

 The type attribute helps to provide the correct behavior and appearance for the input field, making it easier for the user to understand what is expected.

### Without CSS

![Screenshot 2023-02-05 at 3.19.53 PM.png](Introduction%20to%20Flexbox%20f9a4e2b4730a4a75a8eb0f6051ced833/Screenshot_2023-02-05_at_3.19.53_PM.png)

## CSS

```css
.container {
    display: inline-flex;
    flex: 1 1 300px;
    border-radius: 10px;
    border: 1px solid #ccc;
    overflow: hidden;
}

display: inline-flex; sets the container to be an inline-level flex container, which causes the container to behave like an inline element.

flex: 1 1 300px; is a shorthand property for setting the flex-grow, flex-shrink and flex-basis properties. The first value of 1 sets the flex-grow to a value of 1, meaning that the container will grow to fill available space in the parent container. The second value of 1 sets the flex-shrink to a value of 1, meaning that the container will shrink if necessary to fit the parent container. The third value of 300px sets the flex-basis to 300 pixels, which is the starting size of the container before it grows or shrinks.

border-radius: 10px; sets the border-radius of the container to 10 pixels, giving it rounded corners.

border: 1px solid #ccc; sets a 1-pixel-wide solid border to the container, with a color of #ccc (which is a light gray color).

overflow: hidden; sets the overflow of the container to be hidden, meaning that any content that overflows the container will be clipped and not visible.
```

```css
.icon {
	padding: 0.8rem;
}

padding: 0.8rem; The padding property is being set to 0.8rem, which adds space within the element. It adds 0.8rem of space to the top and bottom of the element, and 0.8rem to the left and right.
```

```css
.searchBox {
	border: 0;
	flex: 1;
}

border: 0; The border property is being set to 0, which means no border will be displayed around the element.
flex: 1; The flex property is being set to 1, which means it will take up all the available space in the flex container.
```

```css
.searchButton {
	color: white;
	background: #0f4a8a;
	border: 0;
	padding: 0.8rem;
	border-radius: 8px;
}

color: white; The color property is being set to white, which means the text color of the element will be white.

background: #0f4a8a; The background property is being set to #0f4a8a, which sets the background color of the element to a shade of blue.

border: 0; The border property is being set to 0, which means no border will be displayed around the element.

padding: 0.8rem; The padding property is being set to 0.8rem, which adds space within the element. It adds 0.8rem of space to the top and bottom of the element, and 0.8rem to the left and right.

border-radius: 8px; The border-radius property is being set to 8px, which sets the rounded edges of the element.
```

## With CSS

![Screenshot 2023-02-05 at 4.11.31 PM.png](Introduction%20to%20Flexbox%20f9a4e2b4730a4a75a8eb0f6051ced833/Screenshot_2023-02-05_at_4.11.31_PM.png)

# Example 2: Navigation bars

Next up, we have navigation bars. In this example, we'll create a navigation bar using Flexbox. The bar will consist of several different layouts and be highly responsive on different devices.

## HTML Code

```css
<body>
  <ul class="container">
    <li><a href="#">Home</a></li>
    <li><a href="#">About</a></li>
    <li><a href="#">Services</a></li>
    <li><a href="#">Contact</a></li>
  </ul>
</body>
```

![Screenshot 2023-02-05 at 4.13.17 PM.png](Introduction%20to%20Flexbox%20f9a4e2b4730a4a75a8eb0f6051ced833/Screenshot_2023-02-05_at_4.13.17_PM.png)

## CSS Code

```css
* {
    margin: 0;
    padding: 0;
}

.container {
    background-color: #2b2d42;
    display: flex;
    flex-flow: row wrap;
    justify-content: stretch;
}

.container li {
    list-style-type: none;
}

.container a {
    display: inline-block;
    padding: 25px;
    margin: 0 25px;
    text-align: center;
    text-decoration: none;
    color: #ffffff;
}

.container a:hover {
    background-color: lightsteelblue;
}
```

The given CSS code defines styles for different elements on a webpage. Let's go through each of the rules:

The CSS code sets the universal selector to have a **`margin`**and **`padding`**of 0, meaning there will be no margin or padding on any elements in the HTML.

The **`.container`** class sets the background color, display property to **`flex`**, the flow of the flex container to **`row wrap`**, and the **`justify-content`** property to **`stretch`**, meaning the items in the flex container will be stretched to fill the available space.

The **`.container li`** class sets the **`list-style-type`** to **`none`**, meaning there will be no list markers.

The **`.container a`** class sets the display property to **`inline-block`**, sets a **`padding`** of 25px, **`margin`** of 0 25px, **`text-align`** to center, sets the text decoration to **`none`**, and sets the color to **`#ffffff`**.

The **`.container a:hover`** class sets the background color to **`lightsteelblue`** when the mouse is hovered over a link.
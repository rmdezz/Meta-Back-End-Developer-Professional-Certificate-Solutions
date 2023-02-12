# Pseudo-classes

# Introduction

- Pseudo-class selectors give developers control over what they select and style.
- They allow you to select elements based on their state (e.g. hover, active, visited).
- They improve the interactivity of web pages by styling elements in response to user input.

# General Syntax

- Selector, colon, pseudo-class, and then properties.

# Classification of Pseudo-classes

## User Action States

- Hover: changes style of an element when cursor hovers over it.
- Active: styles an element only while user actively presses and holds mouse button.
- Focus: focuses styling on the element it is used for.

### Example

```css
<!DOCTYPE html>
<html>
  <head>
    <style>
      .mypage:hover {
        color: red;
      }
      .mybutton:active {
        background-color: yellow;
      }
    </style>
  </head>
  <body>
    <p class="mypage">This is a link</p>
    <div>
      <button class="mybutton">Click me</button>
    </div>
  </body>
</html>
```

### Render Output

![Screenshot 2023-02-06 at 11.44.39 AM.png](Pseudo-classes%20c62ce64666f54502ae20c3ae29ec3696/Screenshot_2023-02-06_at_11.44.39_AM.png)

**On hover:**

![Screenshot 2023-02-06 at 11.44.48 AM.png](Pseudo-classes%20c62ce64666f54502ae20c3ae29ec3696/Screenshot_2023-02-06_at_11.44.48_AM.png)

**On button activated:**

![Screenshot 2023-02-06 at 12.15.52 PM.png](Pseudo-classes%20c62ce64666f54502ae20c3ae29ec3696/Screenshot_2023-02-06_at_12.15.52_PM.png)

## Form States

### Disabled and enabled (for buttons)

These pseudo-classes are used for buttons and apply styling to disabled and enabled buttons respectively. Here's an example:

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .btn {
            padding: 10px 20px;
            border: 1px solid rgb(138, 130, 130);
            background-color: beige;
        }

        .btn:disabled {
            background-color: lightgray;
            cursor: not-allowed;
        }
    </style>
    <title>Document</title>
</head>
<body>
    <button class="btn" disabled>Disabled Button</button>
    <button class="btn">Enabled Button</button>
</body>
</html>
```

**Render Output:**

![Screenshot 2023-02-06 at 11.54.19 AM.png](Pseudo-classes%20c62ce64666f54502ae20c3ae29ec3696/Screenshot_2023-02-06_at_11.54.19_AM.png)

The **`padding`** property in CSS defines **the amount of space between an element's content and its border.** It can be specified using either one, two, three, or four values. The values are applied in the following order: top, right, bottom, and left.

```css
.btn {
            padding: 10px 20px;
            border: 1px solid rgb(138, 130, 130);
            background-color: beige;
        }

        .btn:disabled {
            background-color: lightgray;
            cursor: not-allowed;
        }
```

The value of **`padding`** is set to **`10px 20px`**, which means there will be **`10px`** of padding on the top and bottom, and **`20px`** of padding on the right and left.

The default styles of the button include a padding of `**10 pixels**` on top and bottom and `**20 pixels**` on the left and right, a **`1 pixel solid border`** with a color of `**RGB(138, 130, 130)**`, and a **`background color of beige`**.

The second section of the code is defining styles for the same button, but when it is in a **`"disabled"`** state. The styles for the disabled state include a **`background`** color of light gray and a cursor style of **`"not-allowed"`**, which indicates to the user that the button is disabled and cannot be clicked.

### Checked and indeterminate (for checkboxes)

These pseudo-classes are used for checkboxes and apply styling to checked and indeterminate checkboxes respectively. Here's an example:

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <style>
        .checkbox {
            margin-right: 10px;
        }

        .checkbox:checked {
            background-color: lightgreen;
        }

        .checkbox:indeterminate {
            background-color: yellow;
        }
    </style>
    <title>Document</title>
</head>
<body>
    <input type="checkbox" class="checkbox" checked value="Checked">
    <input type="checkbox" class="checkbox" indeterminate value="Indeterminate">
</body>
</html>
```

The **`"indeterminate"`** state is not an actual attribute of an HTML input element with type checkbox, it is a property of the checkbox element in JavaScript. 

To use it, you need to write JavaScript code that sets the "indeterminate" property to true or false based on some condition. This can be done by getting a reference to the element and setting its "indeterminate" property:

```css
document.querySelector('.checkbox').indeterminate = true;
```

### Valid and invalid (for fields like emails and phone numbers)

These pseudo-classes are used for fields like emails and phone numbers and apply styling to valid and invalid fields respectively. Here's an example:

```css
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .field {
            padding: 10px;
            border: 1px solid black;
            background-color: lightgray;
        }

        .field:valid {
            background-color: lightgreen;
        }

        .field:invalid {
            background-color: pink;
        }
    </style>
</head>
<body>
    <input type="email" class="field" required pattern="[a-z0-9._%+-]+@[a-z0-9.-]+\.[a-z]{2,}$">
</body>
</html>
```

**Render Output**

![Screenshot 2023-02-06 at 12.14.06 PM.png](Pseudo-classes%20c62ce64666f54502ae20c3ae29ec3696/Screenshot_2023-02-06_at_12.14.06_PM.png)

![Screenshot 2023-02-06 at 12.14.32 PM.png](Pseudo-classes%20c62ce64666f54502ae20c3ae29ec3696/Screenshot_2023-02-06_at_12.14.32_PM.png)

## Specific Position-Based States

- First-of-type
- Last-of-type
- Nth-of-type
- Nth-last-of-type

### Example

```css
<!DOCTYPE html>
<html>
  <head>
    <style>
      li:first-of-type {
        color: red;
      }
    </style>
  </head>
  <body>
    <ul>
      <li>Adrian</li>
      <li>Mario</li>
    </ul>
  </body>
</html>
```

### Render Output

![Screenshot 2023-02-06 at 11.47.48 AM.png](Pseudo-classes%20c62ce64666f54502ae20c3ae29ec3696/Screenshot_2023-02-06_at_11.47.48_AM.png)

# Conclusion

- There are many types of pseudo-classes with different purposes.
- You can use them to improve the interactivity of your web pages.
- You're encouraged to explore the creative possibilities that pseudo-classes offer.
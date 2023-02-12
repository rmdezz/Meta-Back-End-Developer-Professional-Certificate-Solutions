# Semantic tags in action

The Little Lemon Restaurant has asked to add a new blog page to their website, and it must use semantic HTML to make it accessible and search engine friendly.

# **Setting up the HTML Document Structure**

- The first step is to set up the basic HTML document structure in a file named blog.html.
- The basic semantic structure consists of the header, nav, main, and footer elements.

## **Header Element**

- The header element will display the Little Lemon logo.

```python
<header>
        <img src = "logo.png">
    </header>
```

## Nav Element

- The nav element will describe the navigational structure of the website.
- It will contain navigation links in an ordered list using the ul and li tags.
- The links will be hyperlinked using the anchor tag.

```python
<nav>
        <ul>
            <li>
                <a href="index.html">Home</a>
            </li>
            <li>
                <a href="location.html">Location</a>
            </li>
            <li>
                <a href="blog.html">Blog</a>
            </li>
        </ul>
    </nav>
```

## Main Element

- The main element will feature the main content of the web page, including two blog posts.
- The first blog post will have a title of "20% off this weekend" and a paragraph element with the blog post text.
- The second blog post will have a title of "Our New Menu" and a paragraph element with the blog post text.

```python
<main>
        <h1>Blog</h1>
        <article>
            <h2>20% off this weekend</h2>
            <p>Come down to Little Lemon and your meal will be 20% off!</p>
        </article>
        <article>
            <h2>Our new menu</h2>
            <p>We've updated our menu with new dinners.</p>
        </article>
    </main>
```

## Footer Element

- The footer element will display the copyright notice in a paragraph element.

```python
<footer>
        <p>Copyright Little Lemon</p>
</footer>
```

# Previewing the Blog Page

- After adding the details to each element and saving the file, the blog page can be previewed using live preview.

```python
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Little Lemon</title>
</head>
<body>
    <header>
        <img src = "logo.png">
    </header>
    <nav>
        <ul>
            <li>
                <a href="index.html">Home</a>
            </li>
            <li>
                <a href="location.html">Location</a>
            </li>
            <li>
                <a href="blog.html">Blog</a>
            </li>
        </ul>
    </nav>
    <main>
        <h1>Blog</h1>
        <article>
            <h2>20% off this weekend</h2>
            <p>Come down to Little Lemon and your meal will be 20% off!</p>
        </article>
        <article>
            <h2>Our new menu</h2>
            <p>We've updated our menu with new dinners.</p>
        </article>
    </main>
    <footer>
        <p>Copyright Little Lemon</p>
    </footer>
</body>
</html>
```

![Screenshot 2023-02-04 at 10.01.03 PM.png](Semantic%20tags%20in%20action%20e7dc2611b02e448682b96cf3bdc679ef/Screenshot_2023-02-04_at_10.01.03_PM.png)
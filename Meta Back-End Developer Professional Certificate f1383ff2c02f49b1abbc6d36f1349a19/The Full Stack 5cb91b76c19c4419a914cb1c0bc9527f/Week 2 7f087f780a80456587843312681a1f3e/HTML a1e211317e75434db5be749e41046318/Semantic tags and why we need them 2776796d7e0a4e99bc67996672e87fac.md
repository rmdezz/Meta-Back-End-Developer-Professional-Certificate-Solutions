# Semantic tags and why we need them

As an aspiring developer, you already know that HTML describes the content of a web page. But how do you describe the meaning of a web page? To understand this, think of buttons in an elevator. The vertical arrangement of buttons isn't enough for someone to understand their meaning, so numbers are added to convey the meaning or semantics of the buttons.

In the same way, it's good practice to semantically describe the content of a web page using HTML tags. This allows search engines and accessibility software such as screen readers to understand the contents of a page.

Here are some basic HTML tags you can use to semantically describe your web page:

- Heading tags (e.g. H1) describe headings
- UL and OL tags describe lists

# ****The Structure of an HTML Page****

The structure of an HTML page includes the head and body. Inside the body tag, you can lay out the website using semantic HTML tags to describe each of the sections. For a typical HTML page, the structure can be semantically described using the following tags:

- Header
- Main
- Footer

For example:

```python
<body> 
  <header> 
    <!-- company logo and navigation links --> 
  </header> 
  <nav> 
    <!-- main navigation links --> 
  </nav> 
  <main> 
    <!-- sections and articles --> 
  </main> 
  <footer> 
    <!-- contact information and social media links --> 
  </footer> 
</body>
```

# The Article Element

The article element represents a complete, self-contained composition in a document, page, application, or site that is independently distributable. Examples of this include a forum post, a magazine or newspaper article, a blog entry, a user-submitted comment, an interactive widget, and more.

For example:

```python
<main> 
  <article> 
    <header> 
      <h1>Blog Title</h1> 
      <p>Date and Author of the Blog Post</p> 
    </header> 
    <!-- content of the blog post --> 
  </article> 
</main>
```

# The Section Element

You can use the section element to semantically define individual sections of an article. It's important to note that sections should contain heading elements to semantically describe the section.

For example:

```python
<article> 
  <header> 
    <h1>Blog Title</h1> 
    <p>Date and Author of the Blog Post</p> 
  </header> 
  <main> 
    <section> 
      <h2>Section Heading</h2> 
      <!-- content of the section --> 
    </section> 
  </main> 
</article>
```

# Conclusion

In conclusion, by semantically describing the contents of a web page, your web pages become more accessible, and search engines and accessibility software can easily understand the contents of your well-formed web page.
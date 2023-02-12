# Template inheritance

# ****Introduction to Template Inheritance in Django****

When developing web applications in Django, it's important to follow the key principle of "Don't Repeat Yourself" (DRY). Duplication, whether intentional or not, can lead to maintenance issues and logical contradictions. The framework should deduce as much as possible from as little as possible.

For example, when creating the same header and footer sections across multiple pages for the Little Lemon website, a more efficient method is to build a base template containing all the common elements of the website and assigned them to a block. This block can then be repeated on every web page.

## What is template inheritance?

Template inheritance allows you to split out content by breaking it down into individual components. You can then insert and reuse these components without duplicating work, saving you a lot of time. In this video, you will learn about template inheritance in Django and how developers use it to speed up user interface development.

## Using the Include Tag

The HTML markup on the base page now references the files containing the code for the header and footer sections using the include tag. 

If you need to make an update to either of these files, you'll only need to do it once and not on every page.

Here's an example of how the include tag can be used:

```lua
{% include "header.html" %}

<!-- Page content here -->

{% include "footer.html" %}
```

## Using the Extends Tag

The extends tag is similar to the include tag in syntax and usage, but its purpose and functionality are different. 

**Extend allows you to replace blocks or content from a parent template**, while include simply includes the rendering of a template in the current context.

Here's an example of how the extends tag can be used:

```lua
{% extends "base.html" %}

{% block header %}
  <!-- Add custom header content here -->
{% endblock %}

{% block footer %}
  <!-- Add custom footer content here -->
{% endblock %}
```

# Conclusion

In this video, you learned about how template inheritance can save you time by reusing blocks of content such as headers and footers. You should now have the four Little Lemon pages developed in no time.
# Working with template language

# Introduction

A common requirement in web application development is to add dynamic data inside HTML markup. 

Django provides a way to understand this data through the Django Template Language (DTL). DTL separates the presentation and application logic, making it easier for developers to work with. In this video, you will learn about the different components of DTL and how to use them.

# Variables

Variables are the basic building blocks of DTL. They are surrounded by double curly braces and are evaluated by the template engine. The engine replaces the variable with the result of its evaluation. Variables can be represented by dictionaries, attributes, or list indices. Here's an example of how to use variables in DTL:

```html
Welcome to {{ restaurant_name }} restaurant.
```

# Tags

Tags are the source of logic in DTL. They are created using curly braces and the percentage symbol, and they provide the functionality of control structures like **`if`** and **`for`** loops. Here's an example of using the **`if`** tag:

```html
{% if logged_in %}
    Welcome!
{% else %}
    Please log in.
{% endif %}
```

And here's an example of using the **`for`** loop:

```html
<ul>
{% for item in menu %}
    <li>{{ item.name }} - {{ item.price }}</li>
{% endfor %}
</ul>
```

# Filters

Filters are used to modify the values of variables in DTL. They can be added to variables by using the **`|`** symbol followed by the filter name. Here's an example of using the **`upper`** filter:

```lua
{{ name | upper }}
```

# Comments

Comments are used to provide documentation in DTL. They are created using the curly brace and percentage symbol, and everything between the two tags is ignored by Django. 

Here's an example of a comment in DTL:

```lua
{# This is a comment #}
```

# Conclusion

In this video, you learned about the different components of the Django Template Language and how to use them. Variables, tags, filters, and comments are the building blocks of DTL, and you can use them to create dynamic data for your web applications.
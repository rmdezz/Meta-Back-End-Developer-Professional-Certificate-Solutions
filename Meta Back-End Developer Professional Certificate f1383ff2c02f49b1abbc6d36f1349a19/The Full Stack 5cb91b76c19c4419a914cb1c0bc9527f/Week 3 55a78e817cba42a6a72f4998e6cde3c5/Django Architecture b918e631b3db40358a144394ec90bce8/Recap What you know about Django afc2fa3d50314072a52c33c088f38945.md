# Recap: What you know about Django

In this course, you will be revisiting some key concepts in Django that you learned in the Django course. Here is a quick recap to refresh your memory and prepare you for the rest of this course.

# Overview of Django

- Django is a popular back-end framework used for building web applications.
- It follows the DRY (Don't Repeat Yourself) principle to avoid duplicating code.
- It provides a clean, structured environment to build web applications.
- Advantages of using Django: speed, feature-rich classes, security, scalability.
- Django uses the Model-View-Template (MVT) architecture.

# Model in MVT

- The model handles the database and interacts with it using the QuerySet API.
- You learned how to create models, apply migrations, and interact with the database.
- You also learned how to create forms using the Form API and HTML forms.

# View in MVT

- The view handles web requests and returns web responses.
- You learned how to create views, process HTTP requests, and handle errors.
- You also explored class-based views and the URL configuration file (urls.py).

# Template in MVT

- The template is responsible for rendering the HTML page.
- You learned about the Django Template Language (DTL) and how to create dynamic templates.
- You also learned about template inheritance, variable interpolation, and template tags.

# **Debugging and Testing**

- Debugging is about fixing errors and bugs in the application.
- Testing is about evaluating the quality, reliability, and performance of the application.
- Django has its own debugger, the DEBUG equals True flag, which displays a yellow page error.
- You learned about unit testing and how to use the test case class in the Django test module.

If you feel unsure about anything in this recap, it is recommended that you review the relevant material from the Django course to ensure you are confident and ready for the upcoming activities.

```jsx
Example of Django code:

# models.py
from django.db import models

class Blog(models.Model):
    title = models.CharField(max_length=200)
    body = models.TextField()

    def __str__(self):
        return self.title

# views.py
from django.shortcuts import render
from .models import Blog

def blog_list(request):
    blogs = Blog.objects.all()
    return render(request, 'blog/blog_list.html', {'blogs': blogs})

# urls.py
from django.urls import path
from .views import blog_list

urlpatterns = [
    path('blog/', blog_list, name='blog_list'),
]

# blog_list.html
{% for blog in blogs %}
    <h2>{{ blog.title }}</h2>
    <p>{{ blog.body }}</p>
{% endfor %}
```
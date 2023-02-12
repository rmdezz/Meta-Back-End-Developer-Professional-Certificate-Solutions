# Recap: What you know about forms and ModelForms

# Introduction

Forms play an important role in user interactivity on the Web. They are the backbone of data exchange and allow users to submit data via the POST request. 

Django provides an easy way to generate forms using the form API and model form class. This video will give you an overview of forms, ModelForms, and how they can be generated using the Django framework.

# HTML Forms vs Django Forms

While creating forms using HTML is a conventional approach, it can become tedious and complex when dealing with large forms. In Django, developers can use the form class to represent the expected attributes and render the form elements in HTML.

## HTML Form Example

```jsx
<form action="/" method="post">
  <label for="your_name">Your Name:</label>
  <input type="text" id="your_name" name="your_name" maxlength="100">
  <input type="submit" value="Send Name">
</form>
```

## Django Form Class Example

```jsx
from django import forms

class NameForm(forms.Form):
    your_name = forms.CharField(max_length=100)
```

# ModelForms

**ModelForms go one step further by providing a way to store data in the database.** The process of creating a ModelForm involves creating a model, creating a ModelForm, and configuring the view for processing form data.

## Django Model Example

```jsx
from django.db import models

class Logger(models.Model):
    first_name = models.CharField(max_length=100)
    last_name = models.CharField(max_length=100)
    time_log = models.TimeField()
```

## Django ModelForm Example

```jsx
from django.forms import ModelForm

class LogForm(ModelForm):
    class Meta:
        model = Logger
        fields = ['first_name', 'last_name', 'time_log']
```

# Implementing the View

In the view, an instance of the LogForm class is created and the POST request data is validated and saved to the form.

## View Example

```jsx
from django.shortcuts import render, redirect
from .forms import LogForm

def form_view(request):
    if request.method == 'POST':
        form = LogForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('/')
    else:
        form = LogForm()
    return render(request, 'form.html', {'form': form})
```

# Form Field Types

In Django, the attributes of a form are field class objects that correspond to HTML elements. Some of the most frequently used field types include **`CharField`**, **`IntegerField`**, **`FloatField`**, **`FileField`**, **`EmailField`**, and **`ChoiceField`**.

## CharField

Translates to HTML text input type. 

**Example:**

```jsx
name = forms.CharField(max_length=100)
```

## IntegerField

Similar to a charField but is customized to accept only integer numbers.

**Example:**

```jsx
age = forms.IntegerField()
```

## FloatField

A text input field that validates if the input is a valid float number. 

**Example:**

```jsx
price = forms.FloatField()
```

## FileField

Like the file upload input type on the HTML form. 

**Example:**

```jsx
profile_picture = forms.FileField()
```

## EmailField

A charField that validates if the text entered is a valid email ID. 

**Example:**

```jsx
email = forms.EmailField()
```

## ChoiceField

Used to emulate an HTML form select element. 

**Example:**

```jsx
GENDER_CHOICES = [    ('M', 'Male'),    ('F', 'Female'),]
gender = forms.ChoiceField(choices=GENDER_CHOICES)
```

Choosing the appropriate form field type is important for both the user experience and efficient data processing.
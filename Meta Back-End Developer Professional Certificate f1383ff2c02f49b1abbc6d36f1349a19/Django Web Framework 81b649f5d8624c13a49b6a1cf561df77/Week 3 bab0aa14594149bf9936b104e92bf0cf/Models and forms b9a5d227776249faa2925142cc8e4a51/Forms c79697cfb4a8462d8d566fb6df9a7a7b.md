# Forms

# Introduction

- Web applications use forms to collect data from users through HTML form tags.
- In this video, you will learn about forms in Django, how to use the form class to automatically generate HTML elements and how to use models to automatically generate forms to prevent processing errors.

# Creating forms using HTML

Example of a basic form using HTML to submit a name:

- Use a label to display text describing what the inputs should have.
- Input set to type text accepts input from the end-user.
- Input stores the name.
- Second input of type submit is a button that displays the text send name.
- When the button is pressed, the action will be triggered to make a post request to be processed by the order view.

# Django Form Class

- The form class in Django helps developers create and manage forms easily.
- Define all the expected attributes that will be passed down in the request using the form class.
- Represent the expected attributes and render the form elements in the HTML.

### **Example:**

```python
class NameForm(forms.Form):
    your_name = forms.CharField(max_length=100)
```

- **The advantage of creating forms in this way is that it makes it much easier to manage any changes to the form.**
- **Instead of worrying about the names on inputs matching with the server-side code, this is handled entirely by the form class.**

# Django Model Form

- The model form in Django uses the structure of the model to generate a form.
- Example of a model form:

```python
class ContactForm(forms.ModelForm):
    class Meta:
        model = Contact
        fields = ('name', 'email', 'message')
```

- Using a model form ensures that the data being persisted matches the form being used to collect the data.
- This eliminates potential issues or errors with the data being persisted.

# Conclusion

- In this video, you learned about forms in Django and how to use the form class to automatically generate HTML elements.
- You also learned how to use models to automatically generate forms to prevent potential processing errors.
- These features make managing forms in Django more efficient and less prone to errors
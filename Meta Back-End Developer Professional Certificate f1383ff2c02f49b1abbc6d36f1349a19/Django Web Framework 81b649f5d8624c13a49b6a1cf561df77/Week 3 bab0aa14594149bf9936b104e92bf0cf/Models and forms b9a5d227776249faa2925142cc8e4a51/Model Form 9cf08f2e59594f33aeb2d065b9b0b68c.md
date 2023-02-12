# Model Form

Django provides a way to easily implement models and forms together **to save entries entered in a form to a database.** This can be achieved by using the ModelForm class. The process of creating a ModelForm is similar to creating a model and form, it involves inheriting the ModelForm and implementing it.

# Example:

Let's create a reservation form for the Little Lemon restaurant.

1. Import the model you want to bind with your form.
2. Add implementation details for it using a meta class.
3. Create an instance of that form.

Code for model:

```python
class Reservation(models.Model):
    name = models.CharField(max_length=100)
    date = models.DateField()
    time = models.TimeField()
    
    def __str__(self):
        return self.name
```

Code for form:

```python
class ReservationForm(forms.ModelForm):
    class Meta:
        model = Reservation
        fields = '__all__'
```

Code for view:

```python
def reservation_form(request):
    if request.method == 'POST':
        form = ReservationForm(request.POST)
        if form.is_valid():
            form.save()
            return redirect('home')
    else:
        form = ReservationForm()
    return render(request, 'reservation_form.html', {'form': form})
```

Code for html:

```python
<p>Hello World!</p>

<form action="" method="post", style="background-color: blue;">
    {% csrf_token %}
    {{form.as_p}}
    <input type="submit" value="Submit">
</form>
```

## Explanation

- The **`admin.py`** file is used to register your models with Django's built-in admin interface. This allows you to easily view, add, edit, and delete records from your model in the database through a web interface. By registering your model in the **`admin.py`** file, you can quickly and easily manage the data for your model without having to manually interact with the database.
- As for the HTML file, it is used to render the form on a webpage. When you use the **`{{ form.as_p }}`** template tag, it generates the appropriate HTML markup for each of the fields in the form, including labels, input fields, and validation errors. The **`{% csrf_token %}`** template tag is also used to include a CSRF token in the form, which is used to protect against cross-site request forgery attacks.
- In order for the form to be displayed on the webpage and for the user to interact with it, it is necessary to have a corresponding HTML template. The HTML template also provide the layout for the form, where you can style it or add additional functionality.
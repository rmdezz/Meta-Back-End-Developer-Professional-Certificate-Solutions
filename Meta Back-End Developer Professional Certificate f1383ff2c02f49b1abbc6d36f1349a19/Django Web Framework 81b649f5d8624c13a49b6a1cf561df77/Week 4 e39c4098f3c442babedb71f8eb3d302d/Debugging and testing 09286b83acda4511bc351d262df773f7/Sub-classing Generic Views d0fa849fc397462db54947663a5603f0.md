# Sub-classing Generic Views

In this reading, you’ll learn about the **`class_based`** generic views.

You can implement the view layer with function or class-based views in a Django application. You declare a class by extending the **`django.views.View`** class and define **`get()`** and **`post()`** methods inside it to handle the HTTP requests. The URL pattern connects the path to the class with the **`as_view()`** method of the View class.

A quick example of class view:

```lua
from django.views import View   
class NewView(View):   
    def get(self, request):   
        # View logic will place here   
        return HttpResponse('response')
```

The URL pattern in **[`urls.py`](http://urls.py)** is updated as below:

```lua
#urls.py 
from myapp.views import NewView   
urlpatterns = [   
    path('about/', NewView.as_view()),   
]
```

Django provides class-based generic views to make the development process much easier and faster. In this reading, you’ll discover how the generic views are implemented.

The most frequently used generic views are:

- TemplateView
- CreateView
- ListView
- DetailView
- UpdateView
- DeleteView
- LoginView

## **Difference between Function View and generic view**

Let's take a simple example of rendering a Hello world template. You should render the template as the HTTP response – the return value of the function. 

The view function for this purpose would be as follows:

```lua
from django.shortcuts import render 
from django.http import HttpResponse 

def index(request): 
    template = loader.get_template('myapp/index.html') 
    context={} 
    return HttpResponse(template.render(context, request))
```

As you may have already learned, the app package folder exists inside the project's outer container folder. The **myapp** app is created in the Django project named **myproject**.

In the **`myapp/urls.py`**, define the URL pattern:

```lua
path('/', views.index, name='index')
```

You can include the URL definitions of **`myapp`** in the project's URL configuration:

```lua
urlpatterns = [ 
    . . . , 
    path('myapp/', include('myapp.urls')) 
]
```

Use a **`TemplateView`** class instead. Simply define a class extending it and set the **`template_name`** attribute.

```lua
from django.views.generic.base import TemplateView 

class IndexView(TemplateView): 
    template_name = 'index.html'
```

The corresponding URL pattern should incorporate this:

```lua
path('/', IndexView.as_view(), name='index')
```

## **Advantage of function-based views**

- Simple to implement.
- Easy to read.
- Explicit code flow.
- Straightforward usage of decorators.
- good for one-off or specialized functionality.

## **Disadvantages of function-based views**

- Hard to extend and reuse the code.
- Handling of HTTP methods via conditional branching.

## **Advantages of Class-based views**

- Code reusability.
- DRY — Using CBVs help to reduce code duplication.
- Code can be extended to include more functionalities.
- class with different methods for each http request instead of conditional branching statements inside a single function-based view.
- Built-in generic class-based views.

## **Disadvantages of Class-based views**

- Harder to read.
- Implicit code flow.
- Use of view decorators require extra import or method override.

## **Requirements of a generic view**

- If the view needs a model to be processed, it should be set as the value of model property of the view.
- Each type of view looks for a template name with **`modelname`** suffixed by the type of generic view. For example, for a list view processing employee model, Django tries to find **`employee_list.html`**.
- The generic view is mapped with the URL with **`as_view()`** method of the View class.

Let's now build a subclass for each of the respective generic view classes to perform CRUD operations on the Employee model:

```lua
class Employee(models.Model):   
    name = models.CharField(max_length=100)   
    email = models.EmailField()   
    contact = models.CharField(max_length=15)   
    class Meta:   
        db_table = "Employee"
```

### CreateView

The **`CreateView`** class automates the creation of a new instance of the model. To provide a create view, use the sub-class of **`CreateView`**:

```lua
from django.views.generic.edit import CreateView   

class EmployeeCreate(CreateView):   
    model = Employee    
    fields = '__all__' 
    success_url = "/employees/success/"
```

A model form based on the model structure is created by this view and passed to the **`employeeCreate.html`** template:

```lua
<form method="post"> 
{% csrf_token %} 
<table> 
    {{ form.as_table }} 
</table> 
    <input type="submit" value="Save"> 
</form>
```

The URL path is updated by mapping the **"create/"** path to the **as_view()** method of this class:

```lua
from .views import EmployeeCreate 
urlpatterns = [ 
    . . . 
    path('create/', EmployeeCreate.as_view(), name = 'EmployeeCreate')  , 
]
```

When the client visits this URL, they are presented with the form. The user fills and submits the employee details, which are saved in the Employee table.

### ListView

Django's **`django.views.generic.list`** module contains the definition of **`ListView`** class. Write its sub-class to render the list of model objects.

The **`EmployeeList`** class is similar to the **`CreateView`** sub-class except its base class.

```lua
from django.views.generic.list import ListView  
class EmployeeList(ListView):   
    model = Employee   
    success_url = "/employees/success/"
```

The template required for this view must be named **`employee_list.html`**. Django sends the model object in its context. Using the DTL loop syntax, you can display the list of employees:

```lua
<ul>   
        {% for object in object_list %}   
        <li>Name: {{ object.name }}</li>   
        <li>Email: {{ object.email }}</li>   
        <li>contact: {{ object.contact }}</li>  
        <br/> 
        {% endfor %}   
</ul>
```

If the user visits [http://localhost:/8000/employees/list](http://localhost/8000/employees/list), the browser lists all the rows in the employee table.

### DetailView

The generic DetailView is found in the **`django.views.generic.detail`** module. Now, create its sub-class, **`EmployeeDetail`** (much the same way as **`EmployeeList`**). Note that this view shows the details of an object whose primary key is passed as an argument in the URL. So, add the following path in the app's URL pattern:

```lua
path('show/<int:pk>', EmployeeDetail.as_view(), name = 'EmployeeDetail')
```

Again, the View object fetches the model instance and passes it as a context to the **`employee_detail.html`** template, which displays its attributes with template syntax as follows:

```lua
<h1>Name : {{object.name}}</h1>   

    <p>Email : {{ object.email }}</p>   
    <p>Contact : {{ object.contact }}</p>
```

Assuming the URL visited is **`/employees/1`**, the Employee record with primary key=1 will be displayed.

### UpdateView

This is another generic view, defined in **`django.views.generic.edit`** module. It renders a form in which the new values of the model attributes can be submitted. Set the fields attribute to **`'__all__'`** or to a list of updatable fields.

```lua
from django.views.generic.edit import UpdateView  
class EmployeeUpdate(UpdateView):   
    model = Employee   
    fields = '__all__'   
    success_url = "/employees/success/"
```

Since this view is intended to update the data of a given model instance, its URL path must be configured accordingly:

```lua
path('update/<int:pk>', EmployeeUpdate.as_view(), name = 'EmployeeUpdate')
```

The example URL that invokes this view is **/employees/1**.

The UpdateView class renders the template with its name having **`update_form`** as suffix:

```lua
#employee_update_form.html 
<form method="post"> 
{% csrf_token %} 
<table> 
    {{ form.as_table }} 
</table> 
    <input type="submit" value="Save"> 
</form>
```

### DeleteView

Lastly, the generic view performs the delete operation on a model's given instance. It is present when editing the sub-module of **`django.views.generic`** module:

```lua
from django.views.generic.edit import DeleteView 
class EmployeeDelete(DeleteView):   
    model = Employee   
    success_url = "/employees/success/"
```

You need to pass the primary key of the Employee model to this. So, the URL path is set as:

```lua
path('<delete/int:pk>', EmployeeDelete.as_view(), name = 'EmployeeDelete')
```

The **`employee_confirm_delete.html`** template asks for confirmation from the user before removing the model instance.

```lua
<form method="post"> 
{% csrf_token %}   

    <p>Are you sure you want to delete "{{ object }}"?</p>   

    <input type="submit" value="Confirm">   
</form>
```

In this reading, you got to know about the class-based generic views to perform CRUD operations. Generic views are much easier to write than the **function_based** view, although both have their own advantages and disadvantages.
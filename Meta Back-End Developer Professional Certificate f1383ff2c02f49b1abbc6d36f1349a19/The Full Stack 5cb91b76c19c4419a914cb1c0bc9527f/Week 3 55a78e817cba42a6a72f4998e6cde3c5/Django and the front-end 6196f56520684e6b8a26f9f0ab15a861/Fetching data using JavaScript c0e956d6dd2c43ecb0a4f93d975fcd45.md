# Fetching data using JavaScript

# Introduction

JavaScript is a scripting language that dynamically updates data, multimedia, and other components on a website. When using JavaScript and Django to develop a full-stack application, developers generally follow one of two major approaches: client-first or server-first.

# Client-first Architecture

In client-first architecture, the front-end is the highest priority. With this approach, you first build applications using JavaScript, other frameworks such as React, and processes such as templating and URL routing. Django is then used primarily for coding the interaction with the database and utilizing utility apps such as DRF.

# Server-first Architecture

With server-first architecture, you start by building the components of an application using Django APIs before working with the front end. Django makes it possible to add JavaScript components inside HTML templates and fill in any missing gaps using JavaScript, AJAX, and simple event handling mechanisms. A back-end developer would prefer taking a server-first approach.

# Processing Forms with JavaScript in Django

This video demonstrates how to use JavaScript inside a Django application to process a form. 

For example, you can create a comment section for the Little Lemon food blog using the server-first approach. The form will be updated by an API endpoint which sends a request to the Django view using a POST method. The entered user data or comment is then added to a MySQL database created using models in Django.

# Steps to process Forms and JavaScript

1. Create a Django project, app, and configure the URLs.

![Screenshot 2023-02-08 at 3.04.05 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.04.05_PM.png)

![Screenshot 2023-02-08 at 3.04.17 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.04.17_PM.png)

1. Update database settings for MySQL in the settings.py file.

```jsx
mysql -u root -p
create database blog_db;
show databases;
```

![Screenshot 2023-02-08 at 3.05.20 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.05.20_PM.png)

1. Open the models.py file and create a model called "User Comments" with three attributes: first name, last name, and comment with char field as their form field.
    
    ![Screenshot 2023-02-08 at 3.07.43 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.07.43_PM.png)
    
2. Create a model form called CommentForm in the forms.py file from the User Comments model.
    
    ![Screenshot 2023-02-08 at 3.08.06 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.08.06_PM.png)
    
3. In the views.py file, add the required imports and create a view function called form_view.
    
    ```jsx
    from django.shortcuts import render
    from .forms import CommentForm
    from .models import UserComments
    from django.http import JsonResponse
    
    # Create your views here.
    
    # render and process the form's data and sending the data to the model
    def form_view(request):
    ```
    
4. Create a form object from the CommentForm model form. 
Update the form object with its contents if the request method is POST. 
If the form data is in a valid format, send it to the User Comments model by creating an object and assigning the values received from the POST method to the attributes in the model. 
Return the render function from the view and pass the request, blog.html, and the form data as a dictionary.
    
    ```jsx
    def form_view(request):
        form = CommentForm()
        if request.method == 'POST':
            form = CommentForm(request.POST)
            if form.is_valid():
                cd = form.cleaned_data
                uc = UserComments(
                    first_name = cd['first_name'],
                    last_name = cd['last_name'],
                    comment = cd['comment'],
                )
                uc.save()
                return JsonResponse({'message': 'success'})
        return render(request, 'blog.html', {'form': form})
    ```
    
    <aside>
    🤔 Returning the JSON response class in the views.py file is used to send a response back to the client that made the request **(return JsonResponse({'message': 'success'}))**
    This can be used to return data to the client, such as a success message, or to indicate that an error has occurred. 
    The alert('success') message in the script tag of the blog.html file is only displayed to the user, but it doesn't provide any information to the server about the success of the operation. By returning a JSON response, you can send data back to the client that made the request, which can be used to update the user interface, such as by displaying a message or redirecting to another page. 
    This way, the server can provide more information about the outcome of the operation, and the client can use this information to update the user interface accordingly.
    
    </aside>
    
5. Create a template called blog.html and add the form passed using the render function.
    
    ![Screenshot 2023-02-08 at 3.11.29 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.11.29_PM.png)
    
    ```jsx
    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Document</title>
    </head>
    <body>
        <h1>User Comment</h1>
        <form method="POST" id="form">
            {% csrf_token %}
            {{ form.as_p }}
            **<button type="submit" class="btn btn-primary">submit</button>**
        </form>
    </body>
    </html>
    ```
    
6. Add JavaScript functionality by creating a constant called "Form" and accessing the specific form element from the HTML code.
Use the addEventListener function to handle the form submission and make a POST request using the fetch function.
Process the JSON data received from the fetch function and send a success message.
Reset the form after submission.
    
    ```jsx
    <script>
            const form = document.getElementById('form')
            form.addEventListener("submit", submitHandler)
            function submitHandler(e) {
                e.preventDefault();
                fetch(form.action, {method: 'POST', body: new FormData(form)})
                .then(response => response.json())
                .then(data => {
                    if (data.message == 'success') {
                        alert('success')
                        form.reset()
                    }
                })
            }
        </script>
    ```
    
    ![Screenshot 2023-02-08 at 3.14.48 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.14.48_PM.png)
    
    The **`submitHandler`** function in the javascript code of the **`blog.html`** page is an event handler for the form's submit event.
    
    1. The first line of the function **`e.preventDefault();`** prevents the default behavior of the form's submit event, which is to reload the page.
    2. The **`fetch`** function then makes a **`POST`** request to the URL specified in the **`form.action`** attribute. The **`method`** parameter is set to **`'POST'`** and the **`body`** parameter is set to a **`FormData`** object created from the form element.
    3. The **`then`** function after the fetch call returns the response object, which is then converted into JSON data using **`response.json()`**.
    4. In the next **`then`** function, the JSON data is processed. If the data contains a key **`'message'`** with value **`'success'`**, an alert with the message **`'success'`** is displayed and the form is reset using **`form.reset()`**.
    
    **This function submits the form data to the server and handles the response from the server, updating the page as necessary.**
    
7. Perform migrations and run the server.
    
    ![Screenshot 2023-02-08 at 3.15.09 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.15.09_PM.png)
    

![Screenshot 2023-02-08 at 3.15.27 PM.png](Fetching%20data%20using%20JavaScript%20c0e956d6dd2c43ecb0a4f93d975fcd45/Screenshot_2023-02-08_at_3.15.27_PM.png)
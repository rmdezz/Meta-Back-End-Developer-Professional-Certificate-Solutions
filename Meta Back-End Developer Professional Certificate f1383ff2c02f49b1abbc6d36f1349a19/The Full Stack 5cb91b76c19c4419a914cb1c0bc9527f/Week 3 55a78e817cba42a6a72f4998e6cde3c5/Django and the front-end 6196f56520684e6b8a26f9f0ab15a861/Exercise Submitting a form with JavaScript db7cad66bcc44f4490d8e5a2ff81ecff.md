# Exercise: Submitting a form with JavaScript

# ****Lab assets****

You are provided with a basic setup for a Django environment for the project and app inside the zip file below.

[fAW4B1Y2QjK0d88n46_-NQ_e83be2a5c9b446c9bbf4a29ab41f31f1_Submitting-a-Form-with-JavaScript.zip](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/fAW4B1Y2QjK0d88n46_-NQ_e83be2a5c9b446c9bbf4a29ab41f31f1_Submitting-a-Form-with-JavaScript.zip)

The zip file contains a  template to be used along with supportive files to run the lab.

Note that the virtual environment using **`pipenv`** has been added as a part of the zip file. You must activate the virtual environment and ensure dependencies are installed.

# Objectives

- Set up a JavaScript event to submit form data as a JSON object
- Display a successful form submission alert using JavaScript

# Introduction

Your goal is to submit form data as a JSON object using JavaScript event handling and display submission alert.

# Initial lab instructions

This lab will require you to modify the following files: 

- **views.py**
- **templates/feedback.html**

Starter code has already been added to the following files:

- **settings.py**
- **forms.py**
- **models.py**
- **urls.py (app-level)**
- **urls.py (project-level)**

Additionally, you are required to use the command line console inside the terminal of VS Code.

If not open already, go to **Terminal** on the Menu bar at the top of your screen and select **New Terminal**.

![Untitled](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Untitled.png)

The project named **`myproject`** and an app inside the project called **`myapp`** are ****preconfigured.

Follow the instructions below and ensure you check the output at every step.

<aside>
🤔 **Note:** *Make sure you have installed MySQL on your local machine and that you have set up the root user. In this lab, to keep it simple, you are going to begin with the **root** user credentials. The root user by default has the password which is either **password** or **<blank>**. In case of a blank password, simply press **Enter**. Also, note that the password won’t be visible as it’s being typed.*

</aside>

# Steps

## Step 1

Open the file **`settings.py`** and double-check that the configurations in place for MySQL match the local machine. Create the database name present inside the file to your local machine if not already present. If not added, Django will throw an error.

![Untitled](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Untitled%201.png)

![Screenshot 2023-02-08 at 4.06.33 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_4.06.33_PM.png)

<aside>
🤔 **Note:** *Before you deal with the database, make sure the user created for the database and added inside the **settings.py** file in Django has all the privileges required for accessing and modifying the database.*

</aside>

Run the necessary commands to make sure the user is created and can access the database.

## Step 2

Open the file **`models.py`** and observe the model created for the lab. 

![Screenshot 2023-02-08 at 4.08.07 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_4.08.07_PM.png)

Now open the file **`forms.py`** and note the form created for the purpose of the lab. Take note that form fields present inside both the form and the model are the same. You will understand the reasons for this shortly.

![Screenshot 2023-02-08 at 4.08.35 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_4.08.35_PM.png)

<aside>
🤔 **Note:** There are easier ways of creating forms from a model using **`Meta`** class. The code added here is for clarity.

</aside>

## Step 3

Run the following command to activate the virtual environment:

```jsx
pipenv shell
```

![Screenshot 2023-02-08 at 4.11.10 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_4.11.10_PM.png)

<aside>
🤔 **Note: ***Make sure you run this command in the main working directory containing the **manage.py** file.*

</aside>

## Step 4

To make sure you have the necessary dependencies in place, run the command inside **pipenv**:

```jsx
pipenv install django
pipenv install mysqlclient
```

![Screenshot 2023-02-08 at 4.12.08 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_4.12.08_PM.png)

## Step 5

Now run both commands to perform migrations.

<aside>
🤔 **Note:** *Make sure you are inside the directory that contains **`manage.py`** file.*

</aside>

![Screenshot 2023-02-08 at 4.12.39 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_4.12.39_PM.png)

On running migrations, you may encounter an error such as the one below:

![Untitled](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Untitled%202.png)

If this happens, there is a conflict in the rows present inside your table from your earlier migration. The easy solution is to select option **1** and provide a one-off value such as **null** as a string.

## Step 6

Open the file **`views.py`** to create a configuration for the template you want to create.

The necessary imports are already added and the view function called **`form_view()`** is created.

Follow the steps below to implement the pseudo code and add the code inside the view function:

- if value of **request.method** is **‘POST’**
    - assign value of **MenuForm(request.POST)** to a variable called **form**
    - if **form.is_valid()**
        - assign value of **form.cleaned_data** to a variable called **cd**
        - assign the value of **Menu()** to a variable called **mf** and pass the following arguments inside it:
            - **item_name = cd[‘item_name’]**
            - **category = cd[‘category’]**
            - **description = cd[‘description’]**
        - initialize the **save()** function on the object variable **mf**
        - return **JsonResponse({‘message’ : ‘success’})**
- return **render()** function with following arguments passed inside it:
    - **request**
    - **‘menu_items.html’**
    - **{‘form’: form}**

Save the **views.py** file and ensure the code has no errors.

<aside>
🤔 **Note:** *The template name does not have to be the same as the database name which in this case is* **menu_items**.

</aside>

```jsx
def form_view(request):
		form = MenuForm()
    if request.method == 'POST':
        form = MenuForm(request.POST)
        if form.is_valid():
            cd = form.cleaned_data
            mf = Menu(
                item_name = cd['item_name'],
                category = cd['category'],
                description = cd['description'],
            )
            mf.save()
            return JsonResponse({"message": "success"})
    return render(request, 'menu_items.html', {'form': form})
```

## Step 7

Open the **menu_items.html** file and add the following starter code inside it:

```jsx
<!doctype html>
<html lang="en">
<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
          integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <title>Menu Items </title>
</head>
<body class="bg-light">
<div class="container pt-4">
    <h1>Menu Items </h1>
    <form method="POST" id="form">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</div>
```

<aside>
🤔 **Note:** *Pay attention to the Bootstrap added as a part of the HTML code inside your template.*

</aside>

## Step 8

Below the code added, you will add a code for the **`<script>`** tag. Make sure you also add the closing tag for the script tag.

## Step 9

The code for enabling the JavaScript functionality is written inside the script tag. Follow the pseudo-code below and add the JavaScript code inside the enclosing **`<script>`** tags:

<aside>
🤔 **Note:** *Make sure you add a semi-colon (***;***)* *after each line of code. Unlike Python, JavaScript requires a semi-colon to end a code block.*

</aside>

Create a constant called **form** using the keyword **const** and assign it the value of **document.getElementbyId(‘form’);**.

Call the **addEventListener()** over the **form** variable by using the dot operator and pass the following arguments inside it:

- **“submit”**
- **submitHandler**

Create a function called **submitHandler()** using the keyword function and pass the variable called **e** to it as an argument. 

- Add the following code inside the function:
    - **e.preventDefault()**
    - **fetch()** function with following arguments passed inside it:
        - **form.action**
        - dictionary with following two key-value pairs:
            - method: **‘POST’**
            - body: **new FormData(form)**
    - add **.then()** function and the following code inside it:
        - **response=>response.json()**
    - add **.then()** function and the following argument inside it:
        
        ```jsx
        .then(data=>{
                        if (data.message === 'success') {
                            alert('Success!');
                            form.reset()
                    }
                });
        ```
        

Make sure the code has no errors and save the **menu_items.html** file.

```jsx
<!-- Add the HTML template code -->
<!doctype html>
<html lang="en">
<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css"
          integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">

    <title>Menu Items </title>
</head>
<body class="bg-light">
<div class="container pt-4">
    <h1>Menu Items </h1>
    <form method="POST" id="form">
        {% csrf_token %}
        {{ form.as_p }}
        <button type="submit" class="btn btn-primary">Submit</button>
    </form>
</div>
<!-- Add the JavaScript code inside the <script> tags -->
<script>
    const form = document.getElementById('form');
    form.addEventListener("submit", submitHandler);
    function submitHandler(e) {
        e.preventDefault();
        fetch(form.action, {method: 'POST',body: new FormData(form)})
        .then(response => response.json())
        .then(data=> {
                if (data.message === 'success') {
                    alert('Success!');
                    form.reset()
            }
        });
    }
</script>
```

## Step 10

Add a command to run the server and go to the localhost URL. Observe the web page that renders the form.

```jsx
python3 manage.py runserver
```

## Step 11

Enter the details provided in the text file present inside the zip package.

![Screenshot 2023-02-08 at 4.59.43 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_4.59.43_PM.png)

On entering the form data and pressing the submit button, observe that the **Success!** message is displayed as an alert in your browser. Repeat the process for the remaining two form data entries.

## Step 12

In the terminal, run the command that will enable access to **mysql** and enter the **mysql** shell by passing the **-u** and **-p** flags that will enable the MySQL console to prompt for a password.

**Note:** *The password set for **mysql** here will be the same ****as set for root.*

## Step 13

Run the commands to enter the database you have created for your Django project and enter the table name **myapp_menu** that is generated.

Run the command to observe if the database entry you have created inside the form has been added inside the database.

Alternatively, you can also use a third-party database tool for MySQL to observe the contents of the database.

**Note:** *You will not see any entry in the table if it is empty and the code will need to be updated accordingly.*

![Screenshot 2023-02-08 at 5.00.15 PM.png](Exercise%20Submitting%20a%20form%20with%20JavaScript%20db7cad66bcc44f4490d8e5a2ff81ecff/Screenshot_2023-02-08_at_5.00.15_PM.png)

# Conclusion

In this lab, you have learned how to set up JavaScript events to submit to form data as a JSON object and display an alert on successful form submission.
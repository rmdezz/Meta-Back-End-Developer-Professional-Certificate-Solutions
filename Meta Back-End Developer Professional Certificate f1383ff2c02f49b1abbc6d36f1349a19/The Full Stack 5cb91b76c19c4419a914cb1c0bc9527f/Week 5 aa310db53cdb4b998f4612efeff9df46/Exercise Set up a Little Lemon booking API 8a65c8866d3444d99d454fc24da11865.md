# Exercise: Set up a Little Lemon booking API

# Lab assets

You are provided with a basic setup for the Django environment for the project and app inside the zip file below.

[B-VRtLgrQViscbPCArFZjA_282d52c733ed489383453e3e101d08f1_Set-up-the-Little-Lemon-booking-API.zip](Exercise%20Set%20up%20a%20Little%20Lemon%20booking%20API%208a65c8866d3444d99d454fc24da11865/B-VRtLgrQViscbPCArFZjA_282d52c733ed489383453e3e101d08f1_Set-up-the-Little-Lemon-booking-API.zip)

The zip file contains an updated template to be used along with supportive files to run the lab.

<aside>
🤔 **Note:** *The virtual environment using **pipenv** has been added as a part of the zip file. You must activate the virtual environment and ensure dependencies are installed.*

</aside>

Your goal is to set up an API endpoint to send form data to a MySQL database and return a JSON object to be displayed on the web page.

# Objectives

Create a view to process form data entered in a Django template

Convert form data received from a **`POST`** method into a JSON object and return to a web page

# Introduction

Part one of the assessment included setting up a MySQL database which is far more secure and scalable than the SQLite which was used earlier. Now, in the part two of the final assessment, you have to integrate the booking feature into the existing website.

# Initial lab instructions

This lab will require you to modify the following files: 

- **views.py**
- **forms.py**
- **urls.py (app-level)**
- **templates/bookings.html**
- **templates/book.html**

Starter code has already been added to the following files:

- **settings.py**
- **models.py**
- **urls.py** (app-level)
- **urls.py** (project-level)
- **views.py** (partially complete)

<aside>
🤔 **Note:** *Once you set up the project, make sure you review the contents of all the files and follow the steps accordingly. The zip file added here may contain some additional stylesheets and formatting, so you must use the attached file as the starter code instead of building on your existing project from part one.*

</aside>

You have already built the project named **littlelemon** and added an app inside the project called **restaurant**.

Follow the instructions below and ensure you check the output at every step.

<aside>
🤔 **Note:** *Make sure you have installed MySQL on your local machine and set up the admin user. In this exercise, to keep it simple, you are going to begin with the root user with credentials. The root user by default has the password which is either **password** or **<blank>**. In case of a blank password, simply press **Enter**. The password will not be visible on screen as it’s being typed.*

</aside>

This is part two of the final assessment and it deals with utilizing the Django framework without any JavaScript. You will first create a model form from the model you created earlier and then update the form with some data. You will then process the form data and send it to the front-end as a JSON object.

# Steps

## Step 1

Run the following command to activate the virtual environment:

```jsx
pipenv shell
```

<aside>
🤔 **Note:** *Make sure you run the command in the main working directory containing the **manage.py** file.*

</aside>

## Step 2

To make sure you have the necessary dependencies in place, run the following commands inside pipenv:

```jsx
pipenv install django
pipenv install mysqlclient
```

<aside>
🤔 **Note:** *If you are ****facing problems with using the virtual environment, you can try running the project without using **pipenv**.*

</aside>

## Step 3

Create a file in the **`restaurant`** directory called **`forms.py`** and import the following:  

- The **Booking** model from the file **models.py**.
- The module **forms** from the package **django**

## Step 4

Still inside the **`forms.py`** file, create a class called **`BookingForm`** and pass the **`forms.ModelForm`** as an argument to it.

## Step 5

Inside the class **`BookingForm`**, create another class called **`Meta`** and declare the following attributes inside it:

- **Model** with the value **Booking**
- **Field** with the value **"__all__"**

## Step 6

In the terminal run both commands to perform the migrations.

<aside>
🤔 **Note:** *Make sure you have created the correct MySQL user, assigned privileges, and configured the same database before you perform the migrations.*

</aside>

Run the necessary commands to make sure the user is created and can access the database.

## Step 7

Open the file **`views.py`** and observe the code present inside it for the different views on the Little Lemon website. This was part of the functionality that was added using just the Django framework.

Remove the comments for the **`book()`** view function.

Also remove the commenting for the import statement below:

```jsx
# from .forms import BookingForm
```

Observe the **`book()`** function that contains the functionality to accept the values added inside the form rendered on the page **`book.html`**.

<aside>
🤔 **Note:** *The necessary imports are already added inside the **views.py** file.*

</aside>

## Step 8

Create a view function called **`bookings()`** and pass the request object to it as an argument. Follow the pseudo code below to add the necessary code for processing the form data.

Inside the **`bookings()`** view function, add the following pseudo code:

- Create a variable called **date** and assign it the following value:
    - **request.GET.get('date',datetime.today().date())**
- Create a variable called **bookings** and assign it the following value:
    - Call **objects.all()** on the **Booking** class object.
- Create a variable called **booking_json** and assign it the following value:
    - **serialize()** function called over **serializers**. Pass the following arguments to the **serialize()** function
        - **‘json’**
        - **bookings**
- Return the **render()** function and pass the following arguments to it:
    - **request**
    - **"booking.html"** as a string
    - dictionary containing following key-value pairs:
        - Key: **“bookings”**
        - Value: **booking_json**

Save the **views.py** file and ensure the code has no errors.

```jsx
def bookings(request):
    date = request.get('date', datetime.today().date())
    bookings = Booking.objects.all()
    booking_json = serializers.serialize('json', bookings)
    return render(request, 'booking.html', {"bookings": booking_json})
```

## Step 9

Go to the app-level **urls.py** file and remove the comment for the URL configuration of the view functions below:

- **bookings**
- **book**

## Step 10

Open the file **`book.html**` file present inside the templates folder and update the code as per the instructions below.

Add a heading using the **<h1>** tag that says, **Make a reservation**.

## Step 11

Now step inside the **`<script>`** tags and add the following pseudo code to update the **`book.html`** file.

- Call the log() function on **console** and pass the argument **“Hello”** inside it
- Call the function **getElementById()** on the **document** and pass the string **"id_reservation_date"** to it as an argument.
    - Suffix the code by adding a filter **type="date"** using a dot operator.

```jsx
<script>
  console.log("Hello")
  document.getElementById("id_reservation_date").type = "date";
</script>
```

## Step 12

Now open the **`bookings.html`** file present inside the templates folder and update the code as per the instructions below.

Add a heading using the **`<h1>`** tag that says **`All Reservations`**

## Step 13

Now step inside the **<script>** tags and add the following pseudo code to update the **bookings.html** file.

- Create a constant called **bookings** and assign it the value of **parse()** function called over **JSON**. Pass the following argument inside the **parse()** function:
    - **'{{ bookings|safe }}'**
- Call the **log()** function on console and pass **bookings** to it as an argument.
- Create a constant called **pretty_json** and assign it the value of:
    - **stringify()** function called over JSON and pass the following arguments to it:
        - **bookings**
        - **null**
        - **2**

**Note:** *Observe the code added inside the file **bookings.html** and save the file. Make sure there are no errors present in your code.*

```jsx
<script>
  const bookings = JSON.parse('{{bookings|safe}}')
  console.log(bookings)
  const pretty_json = JSON.stringify(bookings, null, 2)
</script>
```

## Step 14

Open the file **`index.html`** and look for the comment:

- **<!-- Add code here for book -->**

Replace the comment with the following code:

- **<a href="{% url 'book' %}">Book your table now</a>**

## Step 15

Open the **file `_header.html`** inside the templates or partials folder and look for the comments:

- **<!-- Add code here for the book template -->**
- **<!-- Add code here for the reservations template -->**

Replace the comment with the following code:

- **<li><a href="{% url 'book' %}">Book</a></li>**
- **<li><a href="{% url 'bookings' %}">Reservations</a></li>**

## Step 16

Add a command to run the server and go to the localhost URL.

## Step 17

Go to the tab **`Book`** and add three entries inside the form.

## Step 18

Once the entries are updated, go to the tab **Bookings** that you see in the menu bar. You will be able to observe the entries are updated.

<aside>
🤔 **Note:** *This is the same data that has been updated in the database of the Little Lemon website and can be verified in the database.*

</aside>

# Conclusion

This completes part two of the final assessment. You learned how simple form processing can be done with Django and model data can be added and modified. This data can then be converted into a JSON object which is a more web-friendly data format. In Part 3, you will be using this to implement functionalities of JavaScript to create a richer experience in creating a form that accepts reservations for the Little Lemon website.
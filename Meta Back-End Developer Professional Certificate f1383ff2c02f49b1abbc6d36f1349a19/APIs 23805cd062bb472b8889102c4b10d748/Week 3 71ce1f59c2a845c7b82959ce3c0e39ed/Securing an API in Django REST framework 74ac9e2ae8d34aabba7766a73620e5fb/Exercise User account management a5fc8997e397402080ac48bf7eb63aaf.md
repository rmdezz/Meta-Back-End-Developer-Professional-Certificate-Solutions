# Exercise: User account management

## **Step 6:**

Open the **views.py** file.

**Note:** *All the import statements required are already added. Additionally, the class* **RatingsView** *is* *already declared and updated with the relevant code.*

Create a function inside the class **RatingsView** called **get_permissions()** and pass a single argument inside it called **self**.

Inside the **get_permissions()** function, add the following code:

In this exercise, you will use authentication and validation mechanisms inside DRF. You need to do this activity using **VS code** and **Insomnia** on your computer. If you haven't set up your development environment yet, revisit [Installing VS code](https:), [Setting up tools and environment](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/supplement/6thhh) and [Create a Django Project using pipenv](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/sn2Ez/video-subtitles).

## **Objectives**

By the end of this exercise, you will be able to:

- Add form validators to form data
- Perform token and session authentication while using a DRF form
- Use the Djoser and **authtoken** packages for default routes
- Use the Django admin panel for creating new users and tokens

## **Introduction**

The Little Lemon website has grown in popularity since it was launched. While there are many benefits to the website, fake reviews are a cause for concern. The owners understand the need for better security for their review system.

You are tasked with adding some measures to prevent the misuse of the review system on the Little Lemon website.

## **Instructions**

This lab will require you to modify the following files:

- **views.py**
- **serializers.py**
- **settings.py**
- **admin.py**

You must start the development server on the local host and go to the URL to confirm the desired view on the webpage.

When required, Open the **Terminal** by selecting **New Terminal** under **Terminal** on your **VSCode**.

For your convenience, the Django project called **LittleLemon** and Django app called **LittleLemonDRF** have already been created for you. Download the zip file and save the unzipped content inside a project directory on your local machine. Open the project folder inside VS Code and navigate to the directory containing 'Pipfile' inside your command line. If you are unsure how to set up a Django project reference the optional reading about [Creating a Django project](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/supplement/oQrdH) which includes all the necessary steps and code snippets.

**[User account_Lab files**ZIP File](https://d3c33hcgiwev3.cloudfront.net/i2GlsblkSBa3vaQw_aC7Yw_17df8a1d0b54427988d738dc7da8bce1_User-account_Lab-files.zip?Expires=1675555200&Signature=j3IGqKTNoJ6XbdYLLR~TxIQhRTxA-iCxhiJPBz-8o~a1GUyMcEfXbcWRrP1cPTLi1zYRboq0pUrFvHahHw--3ImO7SydQWZgUQRRlPAg1VJd1D-ih-1Qpv9xseTCrMuldXnKEaVU49Pn8jZciThTHizFia-P6Ju92DENX0XwPPg_&Key-Pair-Id=APKAJLTNE6QMUY6HBC5A)

Follow the instructions below and ensure you check the output at every step.

***Note:** The settings for project level and app level* **urls.py** *file have already been updated.*

## **Initial instructions**

Now run a command on Terminal to initialize the pipenv environment such as:

**pipenv shell**

Open the Pipfile created and ensure the dependencies for the project are already added.

Run a command on the Terminal to install the dependencies such as:

**pipenv install**

**Note:** *You should be able to see the prompt inside the Terminal now has a suffix of round brackets. Follow the steps below to complete the exercise.*

## **Step 1:**

Open the **models.py** file and create a class called **Rating** inside it and pass **models.Model** to it as a parameter.

Create the two attributes in the model and assign the respective form fields to them.

Additionally, pass the following arguments to those form fields:

| Attribute | Form field type | Arguments |
| --- | --- | --- |
| menuitem_id | SmallIntegerField |  |
| rating | SmallIntegerField |  |

Now add a third attribute labeled **category**  and assign it the value of **models.ForeignKey()** with the following arguments passed to it:

- **User**
- **on_delete=models.CASCADE**

## **Step 2:**

Create a file called **serializers.py** inside the app level **LittleLemonDRF** directory. Add the code below inside the file:

12

11

10

9

8

5

6

7

2

3

4

1

)

default=serializers.CurrentUserDefault()

queryset=User.objects.all(),

user = serializers.PrimaryKeyRelatedField(

class RatingSerializer (serializers.ModelSerializer):

from django.contrib.auth.models import User

from rest_framework import serializers

from .models import Rating

from rest_framework.validators import UniqueTogetherValidator

**Note:** *The import statements required have already been added. Additionally, the class* **RatingSerializer** *is already declared and updated with the relevant code. Take note of the user variable created and the contents of the code because you will be using it.*

## **Step 3:**

Create another class called **Meta** inside **RatingSerializer** and add the following code inside the class:

- Assign the **Rating** model to a variable called **model**
- Create a **fields** variable and assign a list to it that contains the following three string elements: **user**, **menuitem_id** and **rating**

**Note:** *The order of list elements must be maintained.*

- Create a variable called **validators** and assign to it a list that contains:
    - A **UniqueTogetherValidator** class that has the following arguments passed to it:
        - a **queryset** variable that is assigned the value of **Rating.objects.all()**
        - a **fields** variable that contains three list elements that are strings like: **user**, **menuitem_id** and **rating**
- Create a variable called **extra_kwargs** that has a dictionary assigned to it containing one item that has the following key-value pair:
    - Key: **rating**
    - Value: A dictionary containing the following two items:
        - **max_value** as key and **5** as value
        - **min_value** as key and **0** as value

**Note:** *Make sure you add a comma after the inner dictionary.*

## **Step 4:**

Open the **settings.py** file inside the project-level directory **LittleLemon**.

Locate the code in the screenshot and follow the instructions provided below to update the code:

![https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/5whr8-RNThyz-T2fudfURA_b8e9af6b57c546d482bb2604e02bf6e1_image.png?expiry=1675555200000&hmac=fjhg2t6RAsZeCcS7HGPPgazO68CWwkJNR92hf9wiw-I](https://d3c33hcgiwev3.cloudfront.net/imageAssetProxy.v1/5whr8-RNThyz-T2fudfURA_b8e9af6b57c546d482bb2604e02bf6e1_image.png?expiry=1675555200000&hmac=fjhg2t6RAsZeCcS7HGPPgazO68CWwkJNR92hf9wiw-I)

You will be adding three configurations inside the **REST_FRAMEWORK** this time:

- Create a string called **DEFAULT_AUTHENTICATION_CLASSES** and assign a list to it containing the following items:
    - **rest_framework.authentication.TokenAuthentication**
    - **rest_framework.authentication.SessionAuthentication**

**Note:** *Make sure you add a comma after every list item.*

## **Step 5:**

Now look for the configuration settings for **INSTALLED_APPS** namespace inside the **settings.py** file and update the list with the following string elements:

- **rest_framework.authtoken**
- **djoser**

**Note:** *Make sure you add a comma after every new element added to the list.*

## **Step 6:**

Open the **views.py** file.

**Note:** *All the import statements required are already added. Additionally, the class* **RatingsView** *is* *already declared and updated with the relevant code.*

Create a function inside the class **RatingsView** called **get_permissions()** and pass a single argument inside it called **self**.

Inside the **get_permissions()** function, add the following code:

# Goal

In this exercise, you will use authentication and validation mechanisms inside DRF. You need to do this activity using **VS code** and **Insomnia** on your computer. If you haven't set up your development environment yet, revisit [Installing VS code](https:), [Setting up tools and environment](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/supplement/6thhh) and [Create a Django Project using pipenv](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/lecture/sn2Ez/video-subtitles).

# Objectives

By the end of this exercise, you will be able to:

- Add form validators to form data
- Perform token and session authentication while using a DRF form
- Use the Djoser and **authtoken** packages for default routes
- Use the Django admin panel for creating new users and tokens

# Introduction

The Little Lemon website has grown in popularity since it was launched. While there are many benefits to the website, fake reviews are a cause for concern. The owners understand the need for better security for their review system.

You are tasked with adding some measures to prevent the misuse of the review system on the Little Lemon website.

# Instructions

This lab will require you to modify the following files:  

- **views.py**
- **serializers.py**
- **settings.py**
- **admin.py**

You must start the development server on the local host and go to the URL to confirm the desired view on the webpage.

When required, Open the **Terminal** by selecting **New Terminal** under **Terminal** on your **VSCode**.

For your convenience, the Django project called **LittleLemon** and Django app called **LittleLemonDRF** have already been created for you. 

Download the zip file and save the unzipped content inside a project directory on your local machine. Open the project folder inside VS Code and navigate to the directory containing 'Pipfile' inside your command line. 

If you are unsure how to set up a Django project reference the optional reading about [Creating a Django project](https://www.coursera.org/teach/apis/g98MzcdAEeyduw6ktL3Xvw/content/item/supplement/oQrdH) which includes all the necessary steps and code snippets.

[i2GlsblkSBa3vaQw_aC7Yw_17df8a1d0b54427988d738dc7da8bce1_User-account_Lab-files.zip](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/i2GlsblkSBa3vaQw_aC7Yw_17df8a1d0b54427988d738dc7da8bce1_User-account_Lab-files.zip)

Follow the instructions below and ensure you check the output at every step.

***Note:** The settings for project level and app level* **urls.py** *file have already been updated.*

# Initial instructions

Now run a command on Terminal to initialize the pipenv environment such as:

```python
**pipenv shell**
```

Open the Pipfile created and ensure the dependencies for the project are already added.

Run a command on the Terminal to install the dependencies such as:

```python
**pipenv install**
```

**Note:** *You should be able to see the prompt inside the Terminal now has a suffix of round brackets. Follow the steps below to complete the exercise.*

## Step 1

Open the **models.py** file and create a class called **Rating** inside it and pass **models.Model** to it as a parameter.

Create the two attributes in the model and assign the respective form fields to them.

Additionally, pass the following arguments to those form fields:

| Attribute | Form field type | Arguments |
| --- | --- | --- |
| menuitem_id | SmallIntegerField |  |
| rating | SmallIntegerField |  |

Now add a third attribute labeled **`user`**  and assign it the value of **models.ForeignKey()** with the following arguments passed to it:

- **User**
- **on_delete=models.CASCADE**

```python
from django.db import models
from django.contrib.auth.models import User 

# Create your models here.
class Rating(models.Model):
    menuitem_id = models.SmallIntegerField()
    rating = models.SmallIntegerField()
    category = models.ForeignKey(User, on_delete=models.CASCADE)
```

## Step 2

Create a file called **serializers.py** inside the app level **LittleLemonDRF** directory. Add the code below inside the file:

```python
from rest_framework import serializers 
from .models import Rating 
from rest_framework.validators import UniqueTogetherValidator 
from django.contrib.auth.models import User 
 
 
class RatingSerializer (serializers.ModelSerializer): 
    user = serializers.PrimaryKeyRelatedField( 
    queryset=User.objects.all(), 
    default=serializers.CurrentUserDefault() 
    )
```

**`Note:`** *The import statements required have already been added. Additionally, the class* **RatingSerializer** *is already declared and updated with the relevant code. Take note of the user variable created and the contents of the code because you will be using it.*

## Step 3

Create another class called **Meta** inside **RatingSerializer** and add the following code inside the class:

- Assign the **Rating** model to a variable called **model**
- Create a **fields** variable and assign a list to it that contains the following three string elements: **user**, **menuitem_id** and **rating**

**Note:** *The order of list elements must be maintained.*

- Create a variable called **validators** and assign to it a list that contains:
    - A **UniqueTogetherValidator** class that has the following arguments passed to it:
        - a **queryset** variable that is assigned the value of **Rating.objects.all()**
        - a **fields** variable that contains three list elements that are strings like: **user**, **menuitem_id** and **rating**
- Create a variable called **extra_kwargs** that has a dictionary assigned to it containing one item that has the following key-value pair:
    - Key: **rating**
    - Value: A dictionary containing the following two items:
        - **max_value** as key and **5** as value
        - **min_value** as key and **0** as value

**Note:** *Make sure you add a comma after the inner dictionary.*

```python
class RatingSerializer (serializers.ModelSerializer): 
    user = serializers.PrimaryKeyRelatedField( 
    queryset=User.objects.all(), 
    default=serializers.CurrentUserDefault() 
    )

    class Meta:
        model = Rating
        fields = ['user', 'menuitem_id', 'rating']
        validators = [
            UniqueTogetherValidator(
                queryset=Rating.objects.all(),
                fields=['user', 'menuitem_id', 'rating']
            )
        ]
        extra_kwargs = {
            'rating': {
                'max_value': 5,
                'min_value': 0
            }
        }
```

## Step 4

Open the **`settings.py`** file inside the project-level directory **`LittleLemon`**.

Locate the code in the screenshot and follow the instructions provided below to update the code:

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled.png)

You will be adding three configurations inside the **`REST_FRAMEWORK`** this time:

- Create a string called **`DEFAULT_AUTHENTICATION_CLASSES`** and assign a list to it containing the following string items:
    - **`rest_framework.authentication.TokenAuthentication`**
    - **`rest_framework.authentication.SessionAuthentication`**

**Note:** *Make sure you add a comma after every list item.*

```python
REST_FRAMEWORK = {
    # Add code to assign default authentication classes
    'DEFAULT_AUTHENTICATION_CLASSES': [
        'rest_framework.authentication.TokenAuthentication',
        'rest_framework.authentication.SessionAuthentication',
    ]
}
```

## **Step 5**

Now look for the configuration settings for **INSTALLED_APPS** namespace inside the **settings.py** file and update the list with the following string elements:

- **rest_framework.authtoken**
- **djoser**

**Note:** *Make sure you add a comma after every new element added to the list.*

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    **'rest_framework.authtoken',
    'djoser',
		'LittleLemonDRF', #do not forget this**
]
```

## **Step 6**

Open the **views.py** file.

**Note:** *All the import statements required are already added. Additionally, the class* **RatingsView** *is* *already declared and updated with the relevant code. **(They didn’t)***

Create a function inside the class **RatingsView** called **get_permissions()** and pass a single argument inside it called **self**.

Inside the **get_permissions()** function, add the following code:

```python
from django.shortcuts import render
from .models import Rating
from .serializers import RatingSerializer
from rest_framework import generics
from rest_framework.permissions import IsAuthenticated

# Create your views here.
class RatingsView(generics.ListCreateAPIView):
    queryset = Rating.objects.all()
    serializer_class = RatingSerializer
    def get_permissions(self):
        if self.request.method == 'GET':
            return []
        return [IsAuthenticated()]
```

## Step 7

Run a command to create a **superuser** in Django.

**Tip:** *The command to create a* **superuser** *in Django is:*  **python3 manage.py createsuperuser**

Enter the following details inside the prompts that appear:

- **Username:** admin
- **Email:** admin@littlelemon.com
- **Password:** lemon@789!

## Step 8

Open the file **urls.py** and remove the commenting for the line below:

```python
# path('ratings', views.RatingsView.as_view()),
```

## Step 9

Open the **Terminal** in **VS Code** and run both the commands to perform the migrations.

```python
python3 manage.py makemigrations
python3 manage.py migraet
```

## Step 10

Once the migrations are performed successfully, run the command to start the server on the localhost and go to the URL: **`http://127.0.0.1:8000/admin`**

Enter the details of the credentials for the superuser you have created in **step 8** and log into the Django admin panel. The Django Admin home page should appear as below:

![Screenshot 2023-02-03 at 11.46.08 AM.png](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Screenshot_2023-02-03_at_11.46.08_AM.png)

## Step 11

Click on **Users** and click on **Add User** again. Enter the following details for the new user:

- **Username:** Adrian
- **Email:** adrian@littlelemon.com
- **Password:** lemon@adr!

Press the **Save** button and add another user and enter the following details for the second user:

- **Username:** Mario
- **Email:** mario@littlelemon.com
- **Password:** lemon@mar!

Press the **Save** button once again and add a third user with the following details:

- **Username:** Sana
- **Email:** sana@littlelemon.com
- **Password:** lemon@san!

Press the **Save** button. Ignore the information on the user details screen that appears and press the **Home** button in the left-hand corner of the page.

![Screenshot 2023-02-03 at 12.05.51 PM.png](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Screenshot_2023-02-03_at_12.05.51_PM.png)

## Step 12

Now press the **Tokens** option listed under **Auth Tokens** and press **Add Token**.

## Step 13

Select **Adrian** from the dropdown menu and press the **Save** button.

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%201.png)

A screen will appear that contains Adrian's details along with a unique **key** generated for him. Follow the same process to generate **tokens** for the users **Mario** and **Sana**. Copy and save these tokens because you will use them later on in **Insomnia.**

![Screenshot 2023-02-03 at 12.06.57 PM.png](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Screenshot_2023-02-03_at_12.06.57_PM.png)

## Step 14

Now open the API request client, **`Insomnia`** and perform the following actions:

- Create a **POST** request to the URL: **http://127.0.0.1:8000/api/ratings**

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%202.png)

- Click on Body and select **FORM URL Encoded** as the data structure.

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%203.png)

- Add the following details inside it:
    - menuitem_id: 3
    - rating: 4

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%204.png)

- Under the **Bearer** section add the token value. For example,  for **Adrian** add the token **`4c7cbdf14c6e5b7cd481bb5bd681c89baba49f9d`**
- Also select the checkbox next to **Enabled** and update the Prefix with the value **Token.**

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%205.png)

- Press the **Send** button to generate the **POST** request. It will generate JSON output like in the screenshot below.

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%206.png)

## Step 15

Now keep the value of **`menuitem_id`** unchanged but change the rating to **`5`**. 

It should generate JSON output that is different to before, such as in the screenshot below. The error denotes the throttling limits you have placed on the number of reviews a user can add in a certain amount of time.  It means that any given user can add at most one rating for a specific menu item and a unique set must be created for a combination of a user and a menu item.

```python
Text is wrong.
If you try it, no error is being raised.

It seems like the UniqueTogetherValidator is only checking for the uniqueness of the combination of 'user', 'menuitem_id', and 'rating' for a single user. It's allowing multiple ratings for the same menu item by different users with different rating values.

If you want to limit the number of ratings for a specific menu item by a single user, you should modify the UniqueTogetherValidator to only check for the uniqueness of the combination of 'user' and 'menuitem_id' instead of all three fields.

So change the fields variable of the UniqueTogetherValidator to:
fields = ['user', 'menuitem_id']
```

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%207.png)

## Step 16

Update the **token id** with the user **Sana** and use the same values with which you encountered an error, such as **menuitem_id** with value **3** and a rating value of  **5**. This should update the user review without any issue because it is now a new rating given by another user.

![Untitled](Exercise%20User%20account%20management%20a5fc8997e397402080ac48bf7eb63aaf/Untitled%208.png)

## Step 17

Switch the screen and go back to the webpage on your browser with the URL:

**`http://127.0.0.1:8000/api/ratings`**

Refresh the page to see if the entries for the reviews are updated.

# Concluding thoughts

In this exercise, you learned how to create default routes using Djoser and basic authentication and security mechanisms by implementing throttling functionalities in DRF.
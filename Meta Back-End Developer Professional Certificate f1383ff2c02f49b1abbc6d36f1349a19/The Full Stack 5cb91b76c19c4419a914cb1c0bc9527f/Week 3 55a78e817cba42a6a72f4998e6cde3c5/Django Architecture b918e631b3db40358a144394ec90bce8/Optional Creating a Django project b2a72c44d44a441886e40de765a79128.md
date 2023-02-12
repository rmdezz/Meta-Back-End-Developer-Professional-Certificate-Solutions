# Optional: Creating a Django project

# Introduction

This reading will give you an overview of the steps you should take when creating a Django project while working with VS Code and using pipenv as your virtual environment. The project structure can be vary according to your preferences, but the one suggested is easy to use.

<aside>
🤔 **Note:** *The instructions in this reading may vary slightly from the instructions in the video about creating a Django project because the video presumes a preconfigured Pipfile.*

</aside>

<aside>
🤔 **Note:** *The commands added below are specific to MacOS. The learner will have to make OS specific changes such as using keyword **python** instead of **python3** for Windows OS.*

</aside>

## Step 1

Open VS Code on your computer and click on **`File`**. In the drop-down menu select **`Open Folder`** and select the folder you have created for the project.

![Untitled](Optional%20Creating%20a%20Django%20project%20b2a72c44d44a441886e40de765a79128/Untitled.png)

Now click on **`Terminal`** and select **`New Terminal`** from the drop-down menu. This is the main folder that contains all your files for the Django project you are going to create.

## Step 2

Create a directory for the Django project by running the following command:

```jsx
mkdir LittleLemon
```

## Step 3

Step inside the LittleLemon directory with the command:

```jsx
cd LittleLemon
```

## Step 4

Run the following command to create a project in this directory:

```jsx
django-admin startproject myproject .
```

<aside>
🤔 **Note:** You can run the command above without using the dot(**.**) at the end. However, the relative position of directory and commands executed below must change accordingly. **Without the dot(.), Django creates a nesting directory with a name same as the nested project name.**

</aside>

## Step 5

Run the command to activate **`pipenv`**:

```jsx
pipenv shell
```

<aside>
🤔 **Note:** It is expected that **pipenv** is installed using **pip** on your local machine.

</aside>

## Step 6

Open the file labeled **`Pipfile`** that was created inside the project directory. This file contains details of the dependencies for the project. Update it with the following code and save the file.

![Untitled](Optional%20Creating%20a%20Django%20project%20b2a72c44d44a441886e40de765a79128/Untitled%201.png)

```jsx
[[source]]
url = "https://pypi.org/simple"
verify_ssl = true
name = "pypi"
 
[packages]
django = "*"
djangorestframework = "*"
djangorestframework-xml = "*"
mysqlclient = "*"
 
[dev-packages]
 
[requires]
python_version = "3.9"
```

<aside>
🤔 **Note:** The packages added as dependencies are specific to the lab and functionalities you will require.

</aside>

<aside>
🤔 **Note:** While copy-pasting the file content above, ensure any special characters added automatically are removed. They may appear in yellow or between code blocks in your VSCode.

</aside>

## Step 7

Run this command to install the dependencies using the updated **`Pipfile`**:

```jsx
pipenv install
```

<aside>
🤔 **Note:** *Alternatively, you can also use a command like* **pipenv install django** t*o install specific packages. This will also update the **Pipfile**.*

</aside>

## Step 8

Now run this command to create a Django app:

```jsx
python3 manage.py startapp myapp
```

## Step 9

Run the command to start the server to test if the installation was successful.

```jsx
python3 manage.py runserver
```

Stop the server by pressing **Ctrl** + **C** while you are in the Terminal window.

## Step 10

Create the **`urls.py`** file in the app-level **`LittleLemonDRF`** (myapp) directory.

![Untitled](Optional%20Creating%20a%20Django%20project%20b2a72c44d44a441886e40de765a79128/Untitled%202.png)

Paste the following code inside it:

```jsx
from django.urls import path
from . import views
 
urlpatterns = [
    path('ratings', views.ratings),
]
```

<aside>
🤔 **Note:** *The specific url configurations will differ according  to the views created.*

</aside>

## Step 11

Open the **`urls.py`** file in the project-level directory and update the code as follows:

```jsx
from django.contrib import admin
from django.urls import path, include
 
urlpatterns = [
    path('admin/', admin.site.urls),
    path('home/',include('myapp.urls')),
]
```

<aside>
🤔 **Note:** *The specific url configurations at the project-level will vary according to the name of the app created.*

</aside>

# Conclusion

In this reading, you learned about the initial setup you need to make on your local machine while running VS Code with **pipenv** to create a Django project.
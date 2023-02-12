# Setting up the project

It's time to start preparing for the Capstone Project! In this section, you will review several concepts related to setting up a Django project for Little Lemon restaurant.

# ****Prerequisites****

Before starting, make sure you have the following:

- Python installed on your local machine
- VS Code installed

If you don't have Python installed locally, you can download the Python installer for your operating system and architecture from the official website, then perform the installation by following the installation wizard. Likewise, carry out similar steps to download and install VS Code.

# ****Create a Virtual Environment****

It's recommended to use separate virtual environments for each Django application to avoid conflicts between dependencies. Use the venv module in Python's standard library to create a virtual environment named Little Lemon:

```jsx
python -m venv LittleLemon
```

Activate the virtual environment:

```jsx
source LittleLemon/bin/activate
```

Install the Django framework using the pip installer utility:

```jsx
pip install django
```

# Create a Django Project

To create a Django project, run the following command:

```jsx
django-admin startproject LittleLemon
```

Step inside the project directory:

```jsx
cd LittleLemon
```

Run the following command to start the development server:

```jsx
python manage.py runserver
```

Load the localhost URL from your web browser:

```jsx
http://127.0.0.1:8000/
```

# ****Create an App inside the Project****

To create an app inside the project, run the following command:

```jsx
python manage.py startapp reservations
```

Add the app to the "installed apps" list in the settings.py file:

```jsx
INSTALLED_APPS = [    ...    'reservations',]
```

# ****Push the Code to GitHub****

In your browser, visit the GitHub website, sign up and create a new repository named Little Lemon. Back in your local machine, opened the Git Bash terminal and navigate to the Django project folder.

Initialize the local repository with the following command:

```jsx
git init
```

Add the project to the repository and commit:

```jsx
git add .
git commit -m "Initial commit"
```

Push the local repository to the GitHub repository you have created:

```jsx
git remote add origin https://github.com/<username>/LittleLemon.git
git push -u origin master
```

# Conclusion

With these steps, you will have set up your Django project for Little Lemon restaurant!
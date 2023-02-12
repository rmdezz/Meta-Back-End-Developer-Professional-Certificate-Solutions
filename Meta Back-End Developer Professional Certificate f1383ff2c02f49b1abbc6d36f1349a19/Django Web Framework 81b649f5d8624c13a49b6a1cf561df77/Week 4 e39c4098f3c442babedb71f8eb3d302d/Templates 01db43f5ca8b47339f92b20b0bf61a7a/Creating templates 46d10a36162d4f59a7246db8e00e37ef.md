# Creating templates

# ****Introduction to Django Templates****

- Django provides a convenient way to generate HTML dynamically with templates.
- Templates are text-based documents or Python strings marked up using the Django template language (DTL).
- Templates consist of two types of content: static HTML and dynamic content using the Django template language syntax.

# Render function

- The render function takes three parameters: request, path, and a dictionary of variables.
- The dictionary contains the variables as keys that the template can use to display dynamic data.
- The render function returns a string as part of the HTTP response object that the web page renders.

# Steps to Create a Template

1. Define a view that returns the render function.
2. Update the URL configurations inside URL patterns.
3. Configure the settings for templates and installed apps.
4. Create a HTML page containing static HTML and dynamic data using the Django template language.
5. Pass the name of the template page and dictionary as arguments inside the render function.
    
    ![Screenshot 2023-01-28 at 5.18.35 PM.png](Creating%20templates%2046d10a36162d4f59a7246db8e00e37ef/Screenshot_2023-01-28_at_5.18.35_PM.png)
    
    ![Screenshot 2023-01-28 at 5.18.50 PM.png](Creating%20templates%2046d10a36162d4f59a7246db8e00e37ef/Screenshot_2023-01-28_at_5.18.50_PM.png)
    
    ![Screenshot 2023-01-28 at 5.19.00 PM.png](Creating%20templates%2046d10a36162d4f59a7246db8e00e37ef/Screenshot_2023-01-28_at_5.19.00_PM.png)
    
    ![Screenshot 2023-01-28 at 5.19.15 PM.png](Creating%20templates%2046d10a36162d4f59a7246db8e00e37ef/Screenshot_2023-01-28_at_5.19.15_PM.png)
    
    ![Screenshot 2023-01-28 at 5.19.24 PM.png](Creating%20templates%2046d10a36162d4f59a7246db8e00e37ef/Screenshot_2023-01-28_at_5.19.24_PM.png)
    
    ![Screenshot 2023-01-28 at 5.19.33 PM.png](Creating%20templates%2046d10a36162d4f59a7246db8e00e37ef/Screenshot_2023-01-28_at_5.19.33_PM.png)
    

# Example: Creating an About Page

- Create a view function in the **`views.py`** file and pass the **`request`** object inside it.
- Update the URL configuration files in the **`urls.py`** files at both the project and app levels.
- Create the **`about.html`** page in the **`templates`** folder.
- Create a dictionary object in the **`views.py`** file and pass it to the render function.
- Add dynamic content in the **`about.html`** page using the key from the dictionary object.
- Refresh the page to see the updated content.

# Conclusion

- This video taught how to create a HTML template in Django with some static content in a heading and some dynamic content in a paragraph.
- You learned how to create a template using Django templates and the Django template language.
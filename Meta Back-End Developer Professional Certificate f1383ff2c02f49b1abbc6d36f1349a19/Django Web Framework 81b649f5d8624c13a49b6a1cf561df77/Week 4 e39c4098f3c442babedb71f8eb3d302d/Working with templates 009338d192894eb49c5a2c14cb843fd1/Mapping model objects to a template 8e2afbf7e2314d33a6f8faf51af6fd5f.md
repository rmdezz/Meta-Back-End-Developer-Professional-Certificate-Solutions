# Mapping model objects to a template

One of the reasons Django is popular is that it allows developers to create dynamic website content quickly.

# ****Steps to Display Dynamic Data with a Model Object****

- You will learn how to create a dynamic menu for Little Lemon by passing a model object to a template from a view.
- You will also explore how to loop over an object and display its content using a for-loop with the Django template language.

## Creating the model

- Open the models.py file
- Create a model named "Menu" with the following attributes:
    - Name (CharField)
    - Price (IntegerField)
- Create a dunder string method that will render a string for the objects with the name attribute.

![Screenshot 2023-01-28 at 8.54.38 PM.png](Mapping%20model%20objects%20to%20a%20template%208e2afbf7e2314d33a6f8faf51af6fd5f/Screenshot_2023-01-28_at_8.54.38_PM.png)

## Creating the View Function

- Open the views.py file
- Create another view function called "menu_by_id"
- Import the menu from the models.py file
- Create an object containing all the values present inside the menu model using the method menu.objects.all and assign it to a variable named "new_menu"
- Create a dictionary with a key of "menu" and a value of the variable "new_menu"
- Assign this dictionary to a variable called "new_menu_dict"
- Return a render function that takes three parameters: the request object, the name of the template file, and the dictionary.
    
    ![Screenshot 2023-01-28 at 8.55.57 PM.png](Mapping%20model%20objects%20to%20a%20template%208e2afbf7e2314d33a6f8faf51af6fd5f/Screenshot_2023-01-28_at_8.55.57_PM.png)
    

## Mapping the URL

- Check the mapping in the urls.py file
- The URL inside the path should be set to "menu_card"

**my_app urls.py code:**

![Screenshot 2023-01-28 at 8.56.59 PM.png](Mapping%20model%20objects%20to%20a%20template%208e2afbf7e2314d33a6f8faf51af6fd5f/Screenshot_2023-01-28_at_8.56.59_PM.png)

**project [urls.py](http://urls.py) code:**

![Screenshot 2023-01-28 at 8.57.25 PM.png](Mapping%20model%20objects%20to%20a%20template%208e2afbf7e2314d33a6f8faf51af6fd5f/Screenshot_2023-01-28_at_8.57.25_PM.png)

## Creating the HTML File

- Create an HTML file with the same name as the template file in the render function, "menu_card.html"
- Pass the "menu" key from the dictionary

```lua
{{menu}}
```

## ****Displaying the Dynamic Content****

- Open the browser and navigate to the URL "menu_cards"
- Use the Django template language with a conditional statement to display the items in the menu
- Add a for-loop to iterate over the items in the menu and display the name and price
- Add an else condition to display a message if the menu object is empty
- Wrap the dynamic output with HTML paragraph tags to display each item on a new line
- Demonstrate the dynamic web-page by adding another item to the database using Django administration
    
    ![Screenshot 2023-01-28 at 8.59.52 PM.png](Mapping%20model%20objects%20to%20a%20template%208e2afbf7e2314d33a6f8faf51af6fd5f/Screenshot_2023-01-28_at_8.59.52_PM.png)
    

# Final thoughts

- In this video, you learned how to create a dynamic menu by passing a model object to a template from a view.
- You also explored how to loop over an object and display its contents using a for-loop with a Django template language.
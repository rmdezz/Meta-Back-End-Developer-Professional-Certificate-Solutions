# Dynamic Templates in Django

# Introduction

- In this video, you will learn how to create templates and display dynamic data on a web page using Django
- You will explore how to create templates and use them to get data from a dictionary and display it on a web page
- You will also learn to display data using a for loop with a dictionary inside a template

# Setting up the View function

- Create a view function that takes the request object as a parameter
- Define a dictionary inside the function using open and closed curly braces
- Assign the dictionary to a variable (e.g. menu_item)
- Instead of returning an HTTP response, use the render function
    - Pass three parameters to the render function: request object, name of the HTML file, and the variable holding the dictionary
    
    ![Screenshot 2023-01-28 at 8.13.35 PM.png](Dynamic%20Templates%20in%20Django%20c2de470727f744e38f66cff81425aea5/Screenshot_2023-01-28_at_8.13.35_PM.png)
    

# Creating the Template file

- Create a folder called templates in the project directory
- Inside the templates folder, create a new file (e.g. menu.html)
- Write the code to dynamically display the dictionary object
    - Start by creating double curly braces and inside them, pass the key of the dictionary (e.g. name)
- Make sure Django finds the menu.html file
    - Open the settings file and add the name of the templates folder to the TEMPLATES list
    - Register the app in the INSTALLED_APPS list
    - Open the urls.py file and add the path function to the URL patterns list

![Screenshot 2023-01-28 at 8.14.39 PM.png](Dynamic%20Templates%20in%20Django%20c2de470727f744e38f66cff81425aea5/Screenshot_2023-01-28_at_8.14.39_PM.png)

![Screenshot 2023-01-28 at 8.15.04 PM.png](Dynamic%20Templates%20in%20Django%20c2de470727f744e38f66cff81425aea5/Screenshot_2023-01-28_at_8.15.04_PM.png)

![Screenshot 2023-01-28 at 8.15.45 PM.png](Dynamic%20Templates%20in%20Django%20c2de470727f744e38f66cff81425aea5/Screenshot_2023-01-28_at_8.15.45_PM.png)

![Screenshot 2023-01-28 at 8.16.08 PM.png](Dynamic%20Templates%20in%20Django%20c2de470727f744e38f66cff81425aea5/Screenshot_2023-01-28_at_8.16.08_PM.png)

# Displaying the Dictionary in the Browser

- Run the server and open the URL in the browser
- Navigate to the menu page and notice that the value stored in the dictionary is displayed

# Exploring Django Template Language

- In Django, developers can use templates to make a static page dynamic
- The layout of the page can be structured with HTML and the dynamic data is placed inside double curly braces
- Double curly braces imply dynamic content and it's known as Django Template Language (DTL)

# ****Displaying Dynamic Data with a For Loop****

- Replace the dictionary with an object containing more values
- In the menu.html file, remove the existing code
- Use a for loop to loop over each item in the dictionary
    - Inside the for loop, type **`for item in menu`**
    - Inside double curly braces, type **`item.name`** and **`item.price`**
- Close the for loop
- Add HTML to display each menu item on a new line (e.g. table tags with inline styling)
- Refresh the page and notice that the items from the dictionary are displayed in a table

![Screenshot 2023-01-28 at 8.18.41 PM.png](Dynamic%20Templates%20in%20Django%20c2de470727f744e38f66cff81425aea5/Screenshot_2023-01-28_at_8.18.41_PM.png)

![Screenshot 2023-01-28 at 8.18.53 PM.png](Dynamic%20Templates%20in%20Django%20c2de470727f744e38f66cff81425aea5/Screenshot_2023-01-28_at_8.18.53_PM.png)

# Updating the Dynamic Data

- Add another item with a price to the dictionary
- Save the file and refresh the page
- Notice that the values are updated dynamically on the web page

# Conclusion

- In this video, you learned how to return a web page with dynamic data using templates
- You demonstrated the rendering of dynamic data using a dictionary as the data source
- It's important to know that this data source can be other things like a database or an API
# Restaurant menu API project with DRF

In this video, you'll learn how to create a fully functional CRUD API project with Django Rest Framework (DRF) using a few lines of code.

### **Setting up the Project**

1. Create a new Django app called **`LittleLemonAPI`**
2. Add the app and DRF to the **`settings.py`** file
3. Create a database model with three fields: **`title`**, **`price`**, and **`inventory`**
    
    ![Screenshot 2023-02-01 at 8.27.32 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.27.32_PM.png)
    
4. Create a serializer object to convert model instances into Python datatypes and vice versa
    
    ![Screenshot 2023-02-01 at 8.28.28 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.28.28_PM.png)
    

### **Writing the Code**

1. Open the **`views.py`** file in the **`LittleLemonAPI`** app
2. Import the necessary modules and objects
3. Create a new class, **`MenuItemView`**, that extends the **`ListCreateAPIView`** class from the DRF **`generics`** module
4. Set the **`queryset`** and **`serializer_class`** attributes for the class
    
    ![Screenshot 2023-02-01 at 8.29.04 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.29.04_PM.png)
    
5. Map the class to a URL pattern in the **`urls.py`** file within the **`LittleLemonAPI`** app
    
    ![Screenshot 2023-02-01 at 8.29.22 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.29.22_PM.png)
    
6. Include the **`LittleLemonAPI.urls`** file in the main **`urls.py`** file of your project
    
    ![Screenshot 2023-02-01 at 8.30.41 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.30.41_PM.png)
    
7. Test the code by visiting the **`/api/menu-items`** endpoint in the browser
    
    ![Screenshot 2023-02-01 at 8.31.15 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.31.15_PM.png)
    
    ![Screenshot 2023-02-01 at 8.31.22 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.31.22_PM.png)
    

### **Displaying a Single Record**

1. Create a new class, **`SingleMenuItemView`**, that extends the **`RetrieveUpdateAPIView`** and **`DestroyAPIView`** classes from the DRF **`generics`** module
2. Set the **`queryset`** and **`serializer_class`** attributes for the class
    
    ![Screenshot 2023-02-01 at 8.33.55 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.33.55_PM.png)
    
3. Map the class to a URL pattern in the **`urls.py`** file within the **`LittleLemonAPI`** app
    
    ![Screenshot 2023-02-01 at 8.35.07 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.35.07_PM.png)
    
4. Test the code by visiting the **`/api/menu-items/<item-id>`** endpoint in the browser
    
    ![Screenshot 2023-02-01 at 8.35.21 PM.png](Restaurant%20menu%20API%20project%20with%20DRF%20fa0cffc505c3479cb20a9e455211227b/Screenshot_2023-02-01_at_8.35.21_PM.png)
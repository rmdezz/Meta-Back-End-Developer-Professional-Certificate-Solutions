# Deserialization and validation

Deserialization is the **process of taking data in a specific format, such as JSON, and converting it into an instance of a model in Django.** In DRF, this process is handled by serializers. In this video, we'll learn how to deserialize data in DRF and validate incoming requests.

# Setting up for Deserialization

First, let's start with a project called Little Lemon where we left off. Open the **`views.py`** file in the Little Lemon API and make sure the **`menu_items`** function supports both **`GET`** and **`POST`** requests by adding the **`GET`** and **`POST`** methods to the **`api_view`** decorator.

```python
@api_view(['GET', 'POST'])
def menu_items(request):
    if request.method == 'GET':
        # Code for handling GET request
    else:
        # Code for handling POST request
```

# Deserializing the Request Data

To deserialize the incoming request data, we'll use the **`MenuItemSerializer`** that we created previously. The request data must include all the essential field data, and if any of this information is missing, it should raise an error so that the client can send the request again with the correct payload.

```python
serialized_item = MenuItemSerializer(data = request.data)
serialized_item.is_valid(raise_exception = True)
```

The data validator is built into the serializer, and it can be invoked using the **`is_valid`** method. If the data is valid, the execution will continue, and you can access the validated data using the **`validated_data`** property of the serializer.

```python
validated_data = serialized_item.validated_data
```

# Saving the Deserialized Data

To save the deserialized data, we'll call the **`save`** method on the serializer. This will create a new instance of the **`MenuItem`** model and store it in the database.

```python
serialized_item.save()
```

# Code

```python
from rest_framework.response import Response
from rest_framework.decorators import api_view
from rest_framework import status

@api_view(['GET', 'POST'])
def menu_items(request):
    if request.method == 'GET':
        items = MenuItem.objects.select_related('category').all()
        serializer = MenuItemSerializer(items, many = True, context = {'request': request})
        return Response(serializer.data)
    elif request.method == 'POST':
        serialized_item = MenuItemSerializer(data = request.data)
        serialized_item.is_valid(raise_exception=True)
        serialized_item.save()
        return Response(serialized_item.data, status.HTTP_201_CREATED)
```

# Tips for Deserialization in DRF

It's helpful to create multiple serializers for different purposes and use them separately in your **`GET`** and **`POST`** requests. 

For example, you might have a separate serializer for displaying a list of menu items **(GET request)** and a separate serializer for creating a new menu item **(POST request)**. This way, you can control what fields are shown or hidden in each request.

# Deserialization of Requests with Read-Only Fields

After making a POST request, an error saying "category field is required" is encountered.

## Solution

- Open the "little lemon api serializer.py" file and check the line where the category serializer was included.
    
    ![Screenshot 2023-02-02 at 11.10.23 AM.png](Deserialization%20and%20validation%20e92249b27e174ae2bb42c08a4be7597c/Screenshot_2023-02-02_at_11.10.23_AM.png)
    
- The category field should be read-only, because it is only needed to show the category details in the GET call.
- There are two options to solve the problem:
    1. Comment out the line, which will hide this field from the GET request.
    2. Mark the field as read-only.
- Choose the second option and mark the category field as read-only.
    
    ![Screenshot 2023-02-02 at 11.10.39 AM.png](Deserialization%20and%20validation%20e92249b27e174ae2bb42c08a4be7597c/Screenshot_2023-02-02_at_11.10.39_AM.png)
    
- Make another POST request with JSON payload and verify that everything is working fine.

# Storing requests with Different Category IDs

- The records are stored in the database with the category equals to 1.
    
    ![Screenshot 2023-02-02 at 11.11.32 AM.png](Deserialization%20and%20validation%20e92249b27e174ae2bb42c08a4be7597c/Screenshot_2023-02-02_at_11.11.32_AM.png)
    
- To store a menu item with a different category ID, open the "serializer.py" file and add a new category ID field.
- Add the "category_id" field to the "fields" list in the "Meta" class.
    
    ![Screenshot 2023-02-02 at 11.12.07 AM.png](Deserialization%20and%20validation%20e92249b27e174ae2bb42c08a4be7597c/Screenshot_2023-02-02_at_11.12.07_AM.png)
    
- Revisit the "menu items" endpoint and notice that both the "category" and "category_id" fields are present.
    
    ![Screenshot 2023-02-02 at 11.12.33 AM.png](Deserialization%20and%20validation%20e92249b27e174ae2bb42c08a4be7597c/Screenshot_2023-02-02_at_11.12.33_AM.png)
    
- To hide the "category_id" field from only the GET API calls, make it a write only field.
    
    ```python
    category_id = serializers.IntegerField(write_only = True)
    ```
    
- Make a POST request with an optional category ID and revisit the "menu items" endpoint. Now, there is only one "category" field.
    
    ![Screenshot 2023-02-02 at 11.13.22 AM.png](Deserialization%20and%20validation%20e92249b27e174ae2bb42c08a4be7597c/Screenshot_2023-02-02_at_11.13.22_AM.png)
    

# Conclusion

In this video, we learned how to use deserialization in DRF to convert incoming request data into a model instance, validate it, and store it in the database. 

We also learned a helpful trick for hiding a specific field in a **`GET`** request, which can come in handy in the future.

You also learned how to store the data with different category IDs. You also learned how to make a field read-only in DRF.
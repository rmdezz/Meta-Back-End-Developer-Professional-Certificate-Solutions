# User roles

- In this video, you will learn how to add an extra layer of protection to your API endpoints, called authorization.
- The purpose of authorization is to check if the authenticated user has permission to perform a certain action (e.g. HTTP DELETE or HTTP PATCH).

# Step 1: Create a Django User Group

- Login to the Django admin panel at the URL: /admin
- Click on the "Groups" section and create a new group called "Manager".
    
    ![Screenshot 2023-02-02 at 9.03.40 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.03.40_PM.png)
    
    ![Screenshot 2023-02-02 at 9.03.52 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.03.52_PM.png)
    
- Create two users from the "Users" section, one named "John Doe" who will be the manager and the other named "Jimmy Doe" who will be the customer.
    
    ![Screenshot 2023-02-02 at 9.04.16 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.04.16_PM.png)
    
    ![Screenshot 2023-02-02 at 9.04.27 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.04.27_PM.png)
    
- Assign the "Manager" group to John Doe by editing his profile and selecting the group in the "Groups" section.

# Step 2: Add authorization to your API endpoint

- Open the **`views.py`** file and create a new method called **`manager_view`**.
- Map this method to the URL in the **`urls.py`** file using the **`@api_view`** and **`permission_classes`** decorators.

```python
@api_view()
@permission_classes([IsAuthenticated])
def manager_view(request):
    return Response({"message": "Only manager should see this."})
```

- Get a token for both John Doe and Jimmy Doe by sending an HTTP POST request to the endpoint **`/api/api-token-auth`** with their username and password.
    
    ![Screenshot 2023-02-02 at 9.06.37 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.06.37_PM.png)
    
    ![Screenshot 2023-02-02 at 9.06.49 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.06.49_PM.png)
    
- Send an HTTP GET request to the **`manager_view`** endpoint with John Doe's token and check if the message "Manager should see this" appears.
    
    ![Screenshot 2023-02-02 at 9.07.17 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.07.17_PM.png)
    
- Send another HTTP GET request to the **`manager_view`** endpoint with Jimmy Doe's token and check if an error appears with a 403 status code.
    
    ![Screenshot 2023-02-02 at 9.07.17 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.07.17_PM.png)
    

# Step 3: Implement authorization logic

- In the **`manager_view`** method, check if the authenticated user belongs to the "Manager" group using the following code:
    
    ```python
    @api_view()
    @permission_classes([IsAuthenticated])
    def manager_view(request):
        if request.user.groups.filter(name = "Manager").exists():
            return Response({"message": "Only manager should see this."})
        else:
            return Response({"message": "You are not authorized"}, 403)
    ```
    
- Send another HTTP GET request to the **`manager_view`** endpoint with John Doe's token and check if the message "Manager should see this" appears.
    
    ![Screenshot 2023-02-02 at 9.07.17 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.07.17_PM.png)
    
- Send another HTTP GET request to the **`manager_view`** endpoint with Jimmy Doe's token and check if an error appears with a 403 status code.
    
    ![Screenshot 2023-02-02 at 9.07.06 PM.png](User%20roles%20293560c8abfa4ffdb2feae564c022fec/Screenshot_2023-02-02_at_9.07.06_PM.png)
    

# Conclusion

- You have successfully learned how to add an extra layer of protection to your API endpoints using authorization in Django Rest Framework (DRF).
- By using Django's built-in user group system, you can ensure that only authorized users can access your protected endpoints.
- This knowledge will be useful in future API projects where you need to implement a secure and robust authorization system.
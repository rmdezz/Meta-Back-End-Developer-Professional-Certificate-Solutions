# User account management

# Introduction

- In this video, you'll learn how to register new users using the API endpoints and create a new API for super admin only to assign users to a group or remove them.
- You will not be using JWT in this video, so it's best to clean up JWT specific settings and URL patterns from **`settings.py`** and **`urls.py`**.

# User Registration

- With Djoser, user registration system is made easier.
- Djoser has introduced a few URLs but you're only interested in **`/users`** endpoint.
- This endpoint can accept public HTTP POST calls with email, username, and password without any token.
- The user will be created if the username is not taken.
- To test this endpoint, create a HTTP POST request to the endpoint **`/users`** in insomnia with form URL encoded data as follows:
    - Key: **`username`**
    - Value: **`<username>`**
    - Key: **`email`**
    - Value: **`<email>`**
    - Key: **`password`**
    - Value: **`<password>`**
- You should receive a 200 OK response with the new username and email.
    
    ![Screenshot 2023-02-03 at 11.07.32 AM.png](User%20account%20management%20d75ca52e3c7748ee95a29dd491d4d27f/Screenshot_2023-02-03_at_11.07.32_AM.png)
    

# Super Admin API

- To enable the super admin to add or remove users from groups, you need a special API endpoint.
- Create a new function called **`managers`** in the **`views.py`** file with the API View and permission classes decorator.
- This endpoint can only be accessed with a super admin token, so you need to use the **`IsAdminUser`** permission class.
- Import the **`IsAdminUser`** class from **`rest_framework.permissions`** and add it to the permission classes decorator.
    
    ```python
    from rest_framework.permissions import IsAdminUser
    from django.contrib.auth.models import User, Group
    
    @api_view(['POST'])
    @permission_classes([IsAdminUser])
    def managers(request):
        username = request.data['username']
        if username:
            user = get_object_or_404(User, username=username)
            managers = Group.objects.get(name = "Manager")
            if request.method == 'POST':
                managers.user_set.add(user)
            elif request.method == 'DELETE':
                managers.user_set.remove(user)
            return Response({'message': "ok"})
        return Response({"message": "error"}, status.HTTP_400_BAD_REQUEST)
    ```
    
- To test this endpoint, create a POST request to the endpoint **`/groups/manager/users`** in insomnia with the following data:
    - Key: **`username`**
    - Value: **`<username>`**
        
        ![Screenshot 2023-02-03 at 11.10.30 AM.png](User%20account%20management%20d75ca52e3c7748ee95a29dd491d4d27f/Screenshot_2023-02-03_at_11.10.30_AM.png)
        
        ![Screenshot 2023-02-03 at 11.10.40 AM.png](User%20account%20management%20d75ca52e3c7748ee95a29dd491d4d27f/Screenshot_2023-02-03_at_11.10.40_AM.png)
        
- Use a super admin token for this call. If everything is fine, you should receive an OK message.
- You can also add support for DELETE calls to remove a user from the group by making slight changes to your code.

# Conclusion

In this video, you've learned how to register new users using the Djoser package and how to enable the super admin to add or remove users from groups.
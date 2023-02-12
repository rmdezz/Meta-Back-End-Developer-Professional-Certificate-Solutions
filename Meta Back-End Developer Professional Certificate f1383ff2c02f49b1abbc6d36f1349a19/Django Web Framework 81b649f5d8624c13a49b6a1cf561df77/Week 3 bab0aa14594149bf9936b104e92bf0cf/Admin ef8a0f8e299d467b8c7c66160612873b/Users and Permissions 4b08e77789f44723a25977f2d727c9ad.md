# Users and Permissions

# Creating users using the Django Shell

```python
# Open the Django shell
$ python manage.py shell

# Import the user module
>>> from django.contrib.auth.models import User

# Create a user
>>> user = User.objects.create_user('username', 'email', 'password')

# Find the user
>>> user = User.objects.get(username='username')
```

# Assigning Permissions to Users

```python
# Import the Permission module
>>> from django.contrib.auth.models import Permission

# Add a permission to change the 'menu' model in the 'myapp' app
>>> permission = Permission.objects.get(codename='change_menu', content_type__app_label='myapp')
>>> user.user_permissions.add(permission)
```

# Managing permissions using the Django Admin Interface

1. Login to the Django admin interface
2. Go to the "Groups" section in the "Authentication and Authorization" section
3. Create new groups (e.g. "Reservation Desk", "Website Administrators")
4. Assign permissions to the groups (e.g. "Add, Change, Delete" permissions for the "Reservations" model)
5. Go to the "Users" section in the "Authentication and Authorization" section
6. Create new users (e.g. "Mario", "Maher")
7. Assign personal information, permission level, and group membership to the users
8. Filter users by staff status, superuser status, and group membership

```python
User: Mario
- Personal Info: First Name, Last Name, Email Address
- Permission Level: Superuser
- Group Membership: Admin Users

User: Maher
- Personal Info: First Name, Last Name, Email Address
- Permission Level: Staff
- Group Membership: Reservation Desk
```

# Conclusion

In this video, you learned how to handle user permissions in Django using the Django shell and Django admin interface.
# Setting up API throttling

Throttling is an effective technique to prevent API abuse. It helps you control the frequency of API requests and protects your API infrastructure. In this video, you will learn how to implement throttling in DRF.

# Types of throttling in DRF

DRF has two built-in throttling clusters:

- Anonymous Throttling: Used when there is no token in the API header.
- User Throttling: Used when there is a valid token in the API header.

In addition to these, you can also create custom throttling rules.

# Anonymous Throttling

Here's how to limit the number of API calls for anonymous users in DRF:

- Create a new function in the **`views.py`** file called **`throttle_check`**.
- Import the **`AnonRateThrottle`** class from the **`rest framework.throttling`** module.
- Also, import the **`throttle_classes`** decorator function from the **`rest framework.decorators`** module.
- Add the **`throttle_classes`** decorator to the **`throttle_check`** function, and pass the **`AnonRateThrottle`** class to it.

```python
from rest_framework.throttling import AnonRateThrottle
from rest_framework.decorators import throttle_classes

@throttle_classes([AnonRateThrottle])
def throttle_check(request):
    return Response({"message": "Successful"})
```

- Add the throttle rate in the **`settings.py`** file under the **`DEFAULT_THROTTLE_RATES`** section:
    
    ```python
    REST_FRAMEWORK = {
        'DEFAULT_RENDERER_CLASSES': [
            'rest_framework.renderers.JSONRenderer',
            'rest_framework.renderers.BrowsableAPIRenderer',
            'rest_framework_xml.renderers.XMLRenderer',
        ],
        'DEFAULT_AUTHENTICATION_CLASSES': (
            'rest_framework.authentication.TokenAuthentication',
        ),
        'DEFAULT_THROTTLE_RATES': {
            **'anon': '2/minute', # here**
        }
    }
    ```
    

# User Throttling

Here's how to limit the number of API calls for authenticated users in DRF:

- Create a new function in the **`views.py`** file called **`throttle_check_auth`**.
- Import the **`UserRateThrottle`** class from the **`rest framework.throttling`** module.
- Use the **`UserRateThrottle`** class as the throttling class for this function.

```python
from rest_framework.throttling import UserRateThrottle

@api_view()
@throttle_classes([UserRateThrottle])
def throttle_check_auth(request):
    return Response({"message": "message for the logged in users only"})
```

- Add the throttle rate in the **`settings.py`** file under the **`DEFAULT_THROTTLE_RATES`** section:

```python
'DEFAULT_THROTTLE_RATES' : {
    "anon": "2/minute",
    "user": "5/minute"
}
```

# Custom Throttling

To create a custom throttling policy, follow these steps:

- Create a new file called **`throttles.py`** in your app directory.
- Add the following code to create a new throttle policy:

```python
class TenCallsPerMinute(UserRateThrottle):
    scope = "ten"
```

- Import this class in the **`views.py`** file and use it as the throttle class for any authenticated function calls.
    
    ```python
    from .throttles import TenCallsPerMinute
    
    @throttle_classes([TenCallsPerMinute])
    def throttle_check_auth_custom(request):
        return Response({"message": "Successful"})
    ```
    
- Add the throttle rate in the **`settings.py`** file under the **`DEFAULT_THROTTLE_RATES`**
    
    ```python
    'DEFAULT_THROTTLE_RATES' = {
        "anon": "2/minute",
        "user": "5/minute",
    		"ten": "10/minute",
    }
    ```
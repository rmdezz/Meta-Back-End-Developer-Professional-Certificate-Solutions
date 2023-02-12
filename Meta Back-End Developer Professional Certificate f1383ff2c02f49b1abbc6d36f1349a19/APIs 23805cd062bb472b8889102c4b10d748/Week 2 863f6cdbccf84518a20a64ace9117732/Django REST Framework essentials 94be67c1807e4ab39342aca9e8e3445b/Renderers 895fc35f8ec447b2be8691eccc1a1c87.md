# Renderers

DRF provides support for multiple renderers that allow you to display the output of your APIs in different data formats like JSON, XML, YAML, and JSONP. This makes your API more usable and accessible to a wider range of clients.

# Built-in Renderers

DRF provides some built-in renderers to display the output of your APIs. These are:

- JSON Renderer: Displays the output in JSON format.
- Browsable API Renderer: Displays the browsable API view.

# Third-party Renderers

In addition to the built-in renderers, there are many third-party renderers available to use. Some of the commonly used third-party renderers are:

- XML Renderer: Displays the output in XML format.
- YAML Renderer: Displays the output in YAML format.
- JSONP Renderer: Displays the output in JSONP format.

# Setting the Type of Content

You can set the type of content you want from the API by setting a header in the HTTP request called **`Accept`**. 

For example, to get the output in JSON format, set the value of the **`Accept`** header to **`application/json`**. By default, DRF uses two renderers, the JSON renderer and the Browsable API renderer.

# Turning off the Browsable API Renderer

If you want to turn off the Browsable API renderer and only want to include the JSON content every time, you can do this by adding a new section called **`REST_FRAMEWORK`** in your **`settings.py`** file. 

```python
...

REST_FRAMEWORK = {
    'DEFAULT_RENDERER_CLASSES': [
        'rest_framework.renderers.JSONRenderer',
        'rest_framework.renderers.BrowsableAPIRenderer',
    ]
}
```

![Screenshot 2023-02-02 at 11.35.52 AM.png](Renderers%20895fc35f8ec447b2be8691eccc1a1c87/Screenshot_2023-02-02_at_11.35.52_AM.png)

DRF uses this setting to initialize the renderers. Then, comment out the Browsable API renderer in the **`REST_FRAMEWORK`** section.

```python
REST_FRAMEWORK = {
    'DEFAULT_RENDERER_CLASSES': [
        'rest_framework.renderers.JSONRenderer',
        #'rest_framework.renderers.BrowsableAPIRenderer',
    ]
}
```

![Screenshot 2023-02-02 at 11.35.24 AM.png](Renderers%20895fc35f8ec447b2be8691eccc1a1c87/Screenshot_2023-02-02_at_11.35.24_AM.png)

# Displaying JSON and XML Content

To display JSON and XML content, you can set the value of the **`Accept`** header accordingly. 

For example, to get the output in JSON format, set the value of the **`Accept`** header to **`application/json`** and to get the output in XML format, set the value of the **`Accept`** header to **`application/xml`**.

# Example

Here's an example of how you can use different renderers in DRF. Let's say you have an API endpoint for menu items at **`/api/menu items`**.

## JSON Output

To get the output in JSON format, set the value of the **`Accept`** header to **`application/json`**. You can do this using a tool like Insomnia.

1. Open Insomnia.
2. Create a new HTTP request to the endpoint **`/api/menu items`**.
3. In the header tab, add a new header called **`Accept`** and set its value to **`application/json`**.
4. Send the request.

The output will be displayed in JSON format.

![Screenshot 2023-02-02 at 11.37.26 AM.png](Renderers%20895fc35f8ec447b2be8691eccc1a1c87/Screenshot_2023-02-02_at_11.37.26_AM.png)

## XML Output

To get the output in XML format, you will need to install the **`djangorestframework-xml`** package.

1. Open the terminal and make sure you are in the virtual environment.
2. Install the **`djangorestframework-xml`** package using **`pipenv install djangorestframework-xml`**.
3. In your **`settings.py`** file, add the line **`'rest_framework_xml.renderers.XMLRenderer'`** in the **`REST_FRAMEWORK`** section.

```python
REST_FRAMEWORK = {
    'DEFAULT_RENDERER_CLASSES': [
        'rest_framework.renderers.JSONRenderer',
        'rest_framework.renderers.BrowsableAPIRenderer',
        'rest_framework_xml.renderers.XMLRenderer',
    ]
}
```

1. In Insomnia, set the value of the **`Accept`** header to **`application/xml`**.
    
    ![Screenshot 2023-02-02 at 11.38.22 AM.png](Renderers%20895fc35f8ec447b2be8691eccc1a1c87/Screenshot_2023-02-02_at_11.38.22_AM.png)
    

## HTML

In Insomnia, set the value of the **`Accept`** header to **`text/html`**.

![Screenshot 2023-02-02 at 11.40.30 AM.png](Renderers%20895fc35f8ec447b2be8691eccc1a1c87/Screenshot_2023-02-02_at_11.40.30_AM.png)

# Conclusion

In this video, you learned about the importance of renderers in Django REST framework. You now know how to turn off the Browsable API renderer and display JSON and XML content using the appropriate renderer. By using different renderers, you make your API more usable for a wider range of clients.
# What is Django Rest Framework (DRF)?

Django is a powerful web framework that is great for developing APIs, but it can be time-consuming to develop a robust API. That's where Django Rest Framework (DRF) comes in. DRF is a toolkit that is built on top of the Django web framework, which provides developers with helpful classes and objects to build robust APIs quickly.

![Screenshot 2023-02-01 at 11.55.16 AM.png](What%20is%20Django%20Rest%20Framework%20(DRF)%20a4ad16007a034346b6de2b733f427595/Screenshot_2023-02-01_at_11.55.16_AM.png)

# Benefits of using DRF

## Integration with Django

DRF is a Django utility app that connects your regular Django app to the Django framework and the Object Relational Mapping (ORM) Library, which communicates with the database. Integrating DRF into your existing Django app is straightforward and requires only a few changes in the settings. With these changes, you can have a fully functional Django app powered by DRF almost instantly.

## API Viewer

DRF comes with an API viewer that allows you to send different HTTP methods with data and evaluate the output without needing an external application like Insomnia. This API viewer has limited features, but it's useful when you want to quickly experiment with your APIs.

## Request and Response Objects

DRF comes with its own request and response objects, which are wrappers of the regular Django HTTP response and HTTP request objects. These objects offer more flexibility in processing data in and out of the API.

## HTTP Status Codes

The status module in DRF has a list of human-readable HTTP Status codes. With this module, you don't have to send status codes like 404 or 200 with your responses. Instead, you can use a readable representation like **`Status.HTTP_200_OK`** or **`Status.HTTP_404_NOT_FOUND`**.

## View Sets

**DRF comes with built-in view set classes that make it easy to create a functional CRUD API.** These view sets provide full support for all the necessary HTTP methods out of the box, making it simple to perform basic data manipulation.

## Serialization and Deserialization

![Screenshot 2023-02-01 at 12.01.50 PM.png](What%20is%20Django%20Rest%20Framework%20(DRF)%20a4ad16007a034346b6de2b733f427595/Screenshot_2023-02-01_at_12.01.50_PM.png)

DRF comes with a number of built-in serializers to help with data conversion between models. Serializers also support converting other non-ORM objects, making it simple to convert complex data into native Python data types that can be quickly rendered into JSON, XML, or other content types.

![Screenshot 2023-02-01 at 12.05.12 PM.png](What%20is%20Django%20Rest%20Framework%20(DRF)%20a4ad16007a034346b6de2b733f427595/Screenshot_2023-02-01_at_12.05.12_PM.png)

The process of converting requested data and connecting it back to the existing models is called deserialization. This process also validates user input to ensure no data corruption.

![Screenshot 2023-02-01 at 12.05.42 PM.png](What%20is%20Django%20Rest%20Framework%20(DRF)%20a4ad16007a034346b6de2b733f427595/Screenshot_2023-02-01_at_12.05.42_PM.png)

## API Authentication Systems

DRF also comes with great support for modern API authentication systems. 

Building an authentication layer is a complex process and usually takes time. 

![Screenshot 2023-02-01 at 12.06.04 PM.png](What%20is%20Django%20Rest%20Framework%20(DRF)%20a4ad16007a034346b6de2b733f427595/Screenshot_2023-02-01_at_12.06.04_PM.png)

But with DRF and some supporting packages, you can effortlessly develop an authentication system for your Django app. You can also enable social connections, so your users can authenticate and authorize themselves using an external provider like Facebook and then consume the APIs.

![Screenshot 2023-02-01 at 12.06.23 PM.png](What%20is%20Django%20Rest%20Framework%20(DRF)%20a4ad16007a034346b6de2b733f427595/Screenshot_2023-02-01_at_12.06.23_PM.png)

# Conclusion

In this video, you have learned about the Django Rest Framework (DRF) and some of its benefits to help you quickly develop your API projects. You are now ready to get hands-on with installing and setting up DRF.
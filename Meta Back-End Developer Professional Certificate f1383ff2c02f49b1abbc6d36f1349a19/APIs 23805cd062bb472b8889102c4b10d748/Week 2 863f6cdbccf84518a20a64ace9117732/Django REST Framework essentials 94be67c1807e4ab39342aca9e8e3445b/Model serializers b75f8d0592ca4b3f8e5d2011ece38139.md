# Model serializers

In the previous video, you learned how to use serializers in DRF to convert query sets (single or multiple records) from the database to JSON. 

However, there's an easier way to do this using a special type of serializer called a model serializer. In this video, you will learn how to write less code and convert Django model instances to JSON objects with ease.

# Creating a ModelSerializer

1. Open the main model in the **`models.py`** file. For example, let's consider a **`MenuItem`** model with three fields: **`title`**, **`price`**, and **`inventory`**.
    
    ![Screenshot 2023-02-01 at 11.06.08 PM.png](Model%20serializers%20b75f8d0592ca4b3f8e5d2011ece38139/Screenshot_2023-02-01_at_11.06.08_PM.png)
    
2. Open the **`serializers.py`** file in your Django app. This is where you wrote the serializer in the previous video. Comment out everything and write a new **`MenuItemSerializer`** class using the ModelSerializer class.
    
    ![Screenshot 2023-02-01 at 11.06.32 PM.png](Model%20serializers%20b75f8d0592ca4b3f8e5d2011ece38139/Screenshot_2023-02-01_at_11.06.32_PM.png)
    
3. Open the **`menu-items`** endpoint and everything should work without any issues. You don't need to change any code in the **`views.py`** file.
4. Visit the **`single-item`** endpoint, and everything should work perfectly.

# Modifying Fields in a ModelSerializer

1. To change the name of a field, for example, **`inventory`** to **`stock`**, you can easily do that in the serializer. Remove the **`inventory`** field from the **`fields`** array and add the following line above the **`Meta`** class:

```python
stock = serializers.IntegerField(source='inventory')
```

```python
class MenuItemSerializer(serializers.ModelSerializer):
    stock = serializers.IntegerField(source = 'inventory')
    price_after_tax = serializers.SerializerMethodField(method_name='calculate_tax')
    class Meta:
        model = MenuItem
        fields = ['id', 'title', 'price', 'stock']
```

1. Remember to include the new field in the **`Meta`** class, otherwise you'll see an error.

# Using Calculated Fields in a ModelSerializer

1. You can also use calculated fields in model serializers. Let's introduce a new field called **`price_after_tax`**, which will be an extra 10% of the product price.
2. Add a new method in the **`MenuItemSerializer`** class:

```python
def get_price_after_tax(self, product:MenuItem):
        return round(product.price * Decimal(1.10), 2)
```

1. Link this method as a new field in the serializer by adding the following line above the **`Meta`** class:

```python
price_after_tax = serializers.SerializerMethodField(method_name='calculate_tax')
```

1. Finally, include it in the **`fields`** array in the **`Meta`** class.

```python
from rest_framework import serializers
from .models import MenuItem
from decimal import Decimal

class MenuItemSerializer(serializers.ModelSerializer):
    stock = serializers.IntegerField(source = 'inventory')
    price_after_tax = serializers.SerializerMethodField(method_name='calculate_tax')
    class Meta:
        model = MenuItem
        fields = ['id', 'title', 'price', 'stock', 'price_after_tax']
        
    def calculate_tax(self, product:MenuItem):
        return round(product.price * Decimal(1.1), 2)
```

This is the final code, and when you revisit the endpoints, everything should work fine with the changes.

![Screenshot 2023-02-01 at 11.10.02 PM.png](Model%20serializers%20b75f8d0592ca4b3f8e5d2011ece38139/Screenshot_2023-02-01_at_11.10.02_PM.png)

# Conclusion

In this video, you learned how to use model serializers in the Django Rest Framework to convert model instances quickly and easily to JSON. You also learned how to change the name of a field in the output of an API and how to use calculated fields in a serializer. In the next video, you'll learn how to serialize relationships.
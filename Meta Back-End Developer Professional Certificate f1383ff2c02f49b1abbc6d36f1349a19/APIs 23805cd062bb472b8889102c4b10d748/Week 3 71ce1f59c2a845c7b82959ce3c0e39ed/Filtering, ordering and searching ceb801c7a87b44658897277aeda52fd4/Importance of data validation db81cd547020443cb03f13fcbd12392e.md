# Importance of data validation

# Introduction

Data validation is an important step in every web application because **it ensures that user data is valid and sufficient.** In this reading, you will learn about different validation techniques in DRF.

# Validation

Validation is the process of ensuring that user-submitted data is in the correct format, meets the requirements and is safe to add to the database. 

**The serializers in DRF provide different features which you can use to validate these data while building your APIs.** Before jumping into the details let’s examine some user inputs while adding or modifying the menu items in the Little Lemon API project and how they should be validated.

| Field | Value | Status |
| --- | --- | --- |
| price | 0 | Invalid, because the price of a menu item cannot be 0 |
| stock | negative value | Invalid, because stock of a menu item cannot be lower than 0
 |
| title | Duplicate values | Invalid, because there should not be more than one menu item with the same name or title |

Besides these common validations, **every project has additional requirements.** 

For example, in the Little Lemon project, you can set it so that the price can’t be less than 2.0. And if someone tries to add items with a price below 2.0, it will raise an error. Some of the validation functionalities in DRF will now be discussed.

# Validation in DRF

There are two serializers in the **serializers.py** file, **`MenuItemSerializer`** and **`CategorySerializer`**.

```python
from rest_framework import serializers
from decimal import Decimal
from .models import MenuItem, Category
 
class CategorySerializer (serializers.ModelSerializer):
    class Meta:
        model = Category
        fields = ['id','slug','title']
 
class MenuItemSerializer(serializers.ModelSerializer):
    stock =  serializers.IntegerField(source='inventory')
    price_after_tax = serializers.SerializerMethodField(method_name = 'calculate_tax')
    category_id = serializers.IntegerField(write_only=True)
    category = CategorySerializer(read_only=True)
    class Meta:
        model = MenuItem
        fields = ['id','title','price','stock', 'price_after_tax','category','category_id']
    
    def calculate_tax(self, product:MenuItem):
        return product.price * Decimal(1.1)
```

What follows are four different ways in which to modify some fields in the **MenuItemSerializer**.

## Method 1: Conditions in the field

For the price field, the validation rule is that it should not accept prices less than 2.0. To achieve that result, add the following line before the Meta class in the **MenuItemSerializer**.

```python
price = serializers.DecimalField(max_digits=6, decimal_places=2, min_value=2)
```

If you make a **POST** call to the menu-items endpoint, with the price set to 1, DRF will display the error that the price should be greater than or equal to 2. The validation works.

![Untitled](Importance%20of%20data%20validation%20db81cd547020443cb03f13fcbd12392e/Untitled.png)

## Method 2: Using keyword arguments in the Meta class

If the field is not declared above the Meta field, you can still validate it using keyword arguments in the Meta class. For this method, you need to remove the line you added in the previous section. Add an **extra_kwargs** section in the Meta class with the following code. This **extra_kwargs** section allows you to add additional properties and validations for every field in the serializer.

```python
class Meta:
        model = MenuItem
        fields = ['id','title','price','stock', 'price_after_tax','category','category_id']
        extra_kwargs = {
            'price': {'min_value': 2},
        }
```

If you send the previous **`POST`** call, you will see the same error displayed in Method 1.

You can add additional validation so that the stock cannot go below 0. Add the following line in the **`extra_kwargs`** section in the Meta class.

```python
'stock':{'source':'inventory', 'min_value': 0}
```

Here is the complete code of **`MenuItemSerializer`** class.

```python
class MenuItemSerializer(serializers.ModelSerializer):
    price_after_tax = serializers.SerializerMethodField(method_name = 'calculate_tax')
    category_id = serializers.IntegerField(write_only=True)
    category = CategorySerializer(read_only=True)
    class Meta:
        model = MenuItem
        fields = ['id','title','price','stock', 'price_after_tax','category','category_id']
        extra_kwargs = {
            'price': {'min_value': 2},
            'stock':{'source':'inventory', 'min_value': 0}
        }
    
    def calculate_tax(self, product:MenuItem):
        return product.price * Decimal(1.1)
```

If you send a negative stock value in an HTTP **`POST`** call, DRF will give you an error like in the screenshot below.

![Untitled](Importance%20of%20data%20validation%20db81cd547020443cb03f13fcbd12392e/Untitled%201.png)

## Method 3: Using validate_field() method

Serializers in DRF provide you with another clean way of validating user input by writing **valid_field()** methods, where you replace the field with an actual field name. If the field name is price, the method name has to be **validate_price()**. If the field name is stock, then the method name has to be **validate_stock()**.

Add the following two methods above the Meta class in the **`MenuItemSerializer`.**

```python
def validate_price(self, value):
        if (value < 2):
            raise serializers.ValidationError('Price should not be less than 2.0')
    
def validate_stock(self, value):
        if (value < 0):
            raise serializers.ValidationError('Stock cannot be negative')
```

In these methods, the user-submitted data is passed as a value. As the API developer you need to check if the value meets the requirement, otherwise, raise the **ValidationError** with a message.

Test this by sending a **`POST`** request with invalid values in the price and stock fields. You should get the error message displayed in the screenshot below.

![Untitled](Importance%20of%20data%20validation%20db81cd547020443cb03f13fcbd12392e/Untitled%202.png)

## Method 4: Using the validate() method

You can add a **`validate()`** method in the serializer and validate multiple field values at once. DRF will pass all input values to this method. Here’s an example of how to validate the price and inventory values using a **validate()** method.

**Note:** *To follow this method you need to remove the previous two methods* **`validate_stock`** *and* **`validate_price`** **in the serializer.**

Add the following code above the Meta class in the **MenuItemSerializer**.

```python
def validate(self, attrs):
        if(attrs['price']<2):
            raise serializers.ValidationError('Price should not be less than 2.0')
        if(attrs['inventory']<0):
            raise serializers.ValidationError('Stock cannot be negative')
        return super().validate(attrs)
```

**Note:**  *You used the actual field name for validating the stock which is inventory. If you send a* **POST** request to the **menu-items** *endpoint, you will see an error like the screenshot below.*

![Untitled](Importance%20of%20data%20validation%20db81cd547020443cb03f13fcbd12392e/Untitled%203.png)

## Unique validation

Sometimes API developers need to make sure that there is no duplicate entry made by the clients. In such cases, unique validators become useful. Using this validator, you can ensure the uniqueness of a single field or combination of fields. Let’s examine how to use this validator. 

For a single field, use **`UniqueValidator`** class and for the combination of fields, use **`UniqueTogetherValidator`**.

### UniqueValidator

First, import the classes.

```python
from rest_framework.validators import UniqueValidator
```

or

```python
from rest_framework.validators import UniqueTogetherValidator
```

To make sure that the title field remains unique in the **MenuItems** table, you can add the following code in the **extra_kwargs** section in the Meta class. Here's an example of using **UniqueValidator** for the title field.

```python
extra_kwargs = {
            'title': {
                'validators': [
                    UniqueValidator(
                        queryset=MenuItem.objects.all()
                    )
                ]
            }
        }
```

Or you can add it when declaring a field above Meta class, like this.

```python
title = serializers.CharField(
        max_length=255,
        validators=[UniqueValidator(queryset=MenuItem.objects.all())]
    )
```

If the client sends a duplicate entry, they will see an error as below.

![Untitled](Importance%20of%20data%20validation%20db81cd547020443cb03f13fcbd12392e/Untitled%204.png)

### UniqueTogetherValidator

When you want to use **`UniqueTogetherValidator`** validator, the code will be a little different. Here’s a sample code that will make the combination of **`title`** and **`price`** field unique. With this validation, there will be no duplicate entry of an item with the same price. This code goes directly inside the Meta class.

```python
validators = [
            UniqueTogetherValidator(
                queryset=MenuItem.objects.all(),
                fields=['title', 'price']
            ),
        ]
```

```python
from rest_framework import serializers
from rest_framework.validators import UniqueTogetherValidator
from .models import MenuItem

class MenuItemSerializer(serializers.ModelSerializer):
    class Meta:
        model = MenuItem
        fields = '__all__'
        validators = [
            UniqueTogetherValidator(
                queryset=MenuItem.objects.all(),
                fields=['title', 'price']
            )
        ]
```

If the client sends a duplicate entry, they will see an error as below.

![Untitled](Importance%20of%20data%20validation%20db81cd547020443cb03f13fcbd12392e/Untitled%205.png)

# Conclusion

In this reading, you learned about the importance of data validation and four different methods that you can follow to modify certain fields in the **`MenuItemSerializer`** to validate data in DRF.
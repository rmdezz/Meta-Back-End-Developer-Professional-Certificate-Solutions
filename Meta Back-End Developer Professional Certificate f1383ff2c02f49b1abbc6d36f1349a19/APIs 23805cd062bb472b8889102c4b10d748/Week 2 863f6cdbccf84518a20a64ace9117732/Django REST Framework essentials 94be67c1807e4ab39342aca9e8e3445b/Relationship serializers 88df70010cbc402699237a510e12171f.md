# Relationship serializers

# Introduction

- In a Django project, related data is spread out across multiple tables. To establish relationships between tables, models are used.
- DRF serializers are used to convert models to JSON. In this tutorial, we will look at a new type of serializer called a relationship serializer.

# Models

- In the models.py file, a new Category model is created and connected to the MenuItem model.
- The foreign key relationship is established by creating a foreign key in the MenuItem model, pointing to the Category model.
- When creating the foreign key, the on_delete argument is set to models.PROTECT to prevent deletion of the Category model if there are related MenuItems.

```python
from django.db import models

# Create your models here.
class Category(models.Model):
    slug = models.SlugField()
    title = models.CharField(max_length=255)
    
    def __str__(self) -> str:
        return self.title

class MenuItem(models.Model):
    title = models.CharField(max_length=255)
    price = models.DecimalField(max_digits=6, decimal_places=2)
    inventory = models.SmallIntegerField()
    category = models.ForeignKey(Category, on_delete=models.PROTECT, default=1)
```

# Migrations

- It's important to create migrations and migrate them before proceeding.

If you are getting the following error:

<aside>
🤔 django.db.utils.IntegrityError: The row in table 'LittleLemonAPI_menuitem' with primary key '1' has an invalid foreign key: LittleLemonAPI_menuitem.category_id contains a value '1' that does not have a corresponding value in LittleLemonAPI_category.id.

</aside>

do this:

```python
python3 manage.py shell
from LittleLemonAPI.models import Category
Category.objects.create(slug = 'default', title = 'Ice Cream')
exit()
python3 manage.py migrate
```

# MenuItems endpoint

- The menu items endpoint is visited, but the category information is not present in the API result.
- This is because the category field was not added to the MenuItem serializer's fields list.

## Adding Category to MenuItem Serializer

- In the serializers.py file, the Category model is imported at the top.
- In the MenuItem serializer, the category field is added to the fields list.
- When visiting the menu items endpoint, the category ID is now present in the API result.

```python
class MenuItemSerializer(serializers.ModelSerializer):
    stock = serializers.IntegerField(source = 'inventory')
    price_after_tax = serializers.SerializerMethodField(method_name='calculate_tax')
    category = serializers.StringRelatedField()
    
    class Meta:
        model = MenuItem
        fields = ['id', 'title', 'price', 'stock', 'price_after_tax', 'category']
        
    def calculate_tax(self, product:MenuItem):
        return round(product.price * Decimal(1.1), 2)
```

## Displaying Category to MenuItem Serializer

- To display the category name, a string conversion method is added to the Category model in the models.py file.
    
    ```python
    class Category(models.Model):
        slug = models.SlugField()
        title = models.CharField(max_length=255)
        
        def __str__(self) -> str:
            return self.title
    ```
    
- In the serializers.py file, the Category model is imported and a Category serializer is created.

```python
from .models import Category

class CategorySerializer(serializers.ModelSerializer):
    class Meta:
        model = Category
        fields = ['id', 'slug', 'title']
```

- In the MenuItem serializer, the category field is replaced with the Category serializer.

```python
class MenuItemSerializer(serializers.ModelSerializer):
    stock = serializers.IntegerField(source = 'inventory')
    price_after_tax = serializers.SerializerMethodField(method_name='calculate_tax')
    #category = serializers.StringRelatedField()
    category = CategorySerializer()
    
    class Meta:
        model = MenuItem
        fields = ['id', 'title', 'price', 'stock', 'price_after_tax', 'category']
        
    def calculate_tax(self, product:MenuItem):
        return round(product.price * Decimal(1.1), 2)
```

# Loading Related Data More Efficiently

- In the views.py file, the select_related method is used to load the related Category model in a single SQL query.
- This makes the API more efficient by reducing the number of SQL queries needed to load the related data.

```python
@api_view()
def menu_items(request):
    #items = MenuItem.objects.all()
    items = MenuItem.objects.select_related('category').all()
    serializer = MenuItemSerializer(items, many = True)
    return Response(serializer.data)
```

# Conclusion

- In this tutorial, you learned how to create relationship serializers in DRF to properly display related data.
- You also learned how to tweak the views file to load related data more efficiently.
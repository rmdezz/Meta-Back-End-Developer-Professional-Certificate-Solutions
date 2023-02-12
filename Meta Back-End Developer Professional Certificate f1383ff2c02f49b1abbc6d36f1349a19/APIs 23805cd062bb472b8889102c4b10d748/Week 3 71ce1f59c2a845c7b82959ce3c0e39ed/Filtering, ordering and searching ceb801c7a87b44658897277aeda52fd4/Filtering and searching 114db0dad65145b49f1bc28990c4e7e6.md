# Filtering and searching

Almost all modern apps and websites provide users with a search function. To make this possible for the Little Lemon website and app, you need to adjust your API endpoints. In this section, you will learn about implementing searching and filtering in your API.

# Filtering

When a client application makes an HTTP call to the menu items endpoint, it will display all items along with their categories. But what if a visitor only wants to view items from the appetizers category or only the main dishes, rather than everything at once? Perhaps a visitor prefers to view only items that are within a specific price range, such as $7-$15.

Filtering allows the client applications to get a subset of the results from your API based on some criteria. For example, all the menu items from the appetizers or desserts category. There are two options to approach this:

1. The client application processes the data and manages all filtering on its end.
2. The API developer processes the conditions on the server and delivers results matching those criteria.

The first approach is easier to develop, but it comes with a price. You have to pull all the records from the database every time, which is not sustainable when there are thousands of records or even millions of records.

On the other hand, the second approach will take some extra time to develop but it puts less load on the server and reduces the development time for the client applications.

```python
# Client application approach
http://localhost:8000/menu-items/

# Server approach
http://localhost:8000/menu-items/?category=appetizers&price=7-15
```

In the server approach, the client applications can pass a query string to the menu items endpoint with the query string, such as:

- **`category`**: **`appetizers`** or **`desserts`**
- **`price`**: **`7-15`**

Here's an example of how to implement filtering in the **`views.py`** file:

```python
@api_view(['GET', 'POST'])
def menu_items(request):
    if request.method == 'GET':
        #items = MenuItem.objects.all()
        items = MenuItem.objects.select_related('category').all()
        
        category_name = request.query_params.get('category')
        to_price = request.query_params.get('to_price')
        
        if category_name:
            items = items.filter(category__title = category_name)
        if to_price:
            items = items.filter(price = to_price)
            
        serializer = MenuItemSerializer(items, many = True, context = {'request': request})
        return Response(serializer.data)
    elif request.method == 'POST':
        serialized_item = MenuItemSerializer(data = request.data)
        serialized_item.is_valid(raise_exception=True)
        serialized_item.save()
        return Response(serialized_item.data, status.HTTP_201_CREATED)
```

# Searching

If a client application supplies a search parameter followed by some characters, you will perform a search and return those menu items whose names start with or contain those characters.

Here's an example of how to implement searching in the views.py file:

```python
@api_view(['GET', 'POST'])
def menu_items(request):
    if request.method == 'GET':
        #items = MenuItem.objects.all()
        items = MenuItem.objects.select_related('category').all()
        
        category_name = request.query_params.get('category')
        to_price = request.query_params.get('to_price')
        **search = request.query_params.get('search')**
        
        if category_name:
            items = items.filter(category__title = category_name)
        if to_price:
            items = items.filter(price = to_price)
        **if search:
            items = items.filter(title__startswith = search)**
            
        serializer = MenuItemSerializer(items, many = True, context = {'request': request})
        return Response(serializer.data)
    elif request.method == 'POST':
        serialized_item = MenuItemSerializer(data = request.data)
        serialized_item.is_valid(raise_exception=True)
        serialized_item.save()
        return Response(serialized_item.data, status.HTTP_201_CREATED)
```

In the example above, the search parameter is retrieved from the query string by calling **`request.query_params.get("search")`**. Then, the **`items`** queryset is filtered by name that starts with the search characters by calling **`items.filter(name__startswith=search)`**.

If you want to search if those characters are present anywhere in the name, you just change the field lookup condition to **`contains`**. 

To make those searches case insensitive, the field lookup condition will be **`icontains`** instead of **`contains`**. There is also a case-insensitive version of **`startswith`**, which is **`istartswith`**.
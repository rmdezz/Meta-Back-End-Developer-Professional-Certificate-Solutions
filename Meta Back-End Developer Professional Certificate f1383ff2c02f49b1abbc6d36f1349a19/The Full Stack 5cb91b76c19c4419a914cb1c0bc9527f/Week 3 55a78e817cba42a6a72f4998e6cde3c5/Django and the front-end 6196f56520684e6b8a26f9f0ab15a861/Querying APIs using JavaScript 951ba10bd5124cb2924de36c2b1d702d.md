# Querying APIs using JavaScript

# Introduction

After the lesson on JavaScript you know you can do exciting things with it. You can use it for client-side programming, to make a web application interactive or to send and receive data from the server. **JavaScript really is the default choice when it comes to front-end programming.**

But it can also be used for back-end purposes and in this reading you will learn how to use JavaScript to fetch and send data to an API using the native fetch function.

# ****Native solution versus third-party libraries****

When it comes to fetching data from APIs you might ask yourself, should I use the native fetch function **`XMLHttpRequest`** object, or should I go with libraries like jQuery or Axios? Let’s contextualize the question with some background information.

Previously, fetching data from APIs with **`XMLHttpRequest`** object was difficult because you have to write quite a lot of code to make a simple request. But, at the time, there was no alternative option. Then came third-party libraries that work as a wrapper around **`XMLHttpRequest`** and which provide a simpler interface. These libraries quickly became popular. Later versions of JavaScript came with another native API called fetch, which is powerful, simple and easy to use.

Though using the fetch API is easy, you still have to manually adjust a few things and write extra code for error checking and header processing. This is why libraries like Axios are still popular because they provide a simpler interface and automatically take care of a lot of issues so that you don’t have to write so much code. **Ultimately, you can use either the native fetch API or Axios library.** Both are viable options since both solve the problem of fetching data from APIs in a straightforward manner.

Now let’s explore how you can make **`GET`**, **`POST`**, **`PUT`**, **`PATCH`** and **`DELETE`** calls using the fetch API and how to make authenticated calls using tokens.

# Making a GET call

Placing a **`GET`** call using fetch is simple. All you have to do is make the call, convert the response to JSON or text and then process it any way you want. Here is the output from the **`menu-items`** endpoint of the Little Lemon restaurant app that was used in the course on APIs. Use the following code to make a **`GET`** call to this endpoint:

```jsx
fetch('http://127.0.0.1:8000/api/menu-items')
    .then(response => response.json())
    .then(data => {
        console.log(data)
    })
```

# ****POST, PUT and PATCH Calls****

How do you make a **`POST`** call with data using the fetch API? You have to convert the JSON payload that contains all the data to a string using the  **`JSON.stringify()`** function and pass it as body in the second argument to the fetch function. It’s also a good practice to add **`Accept`** and **`Content`** type headers while making the API calls.

Here is the sample code that creates a new menu item by making a **`POST`** call to the

**`http://127.0.0.1:8000/api/menu-items`** endpoint.

```jsx
const payload = {
    "title": "Ambrosia Ice cream",
    "price": 5.00,
    "inventory": 100
}
const endpoint = 'http://127.0.0.1:8000/api/menu-items'
fetch(endpoint,
    {
        method: 'POST',
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
        },
        body: JSON.stringify(payload)
    })
    .then(response => response.json())
    .then(data => {
        console.log(data)
    })
```

For **`PUT`** and **`PATCH`** calls, you just change the method from **`POST`** to **`PUT`** or **`PATCH`**. Everything else remains the same.

# DELETE calls

For **`DELETE`** calls, change the method to **`DELETE`** and that’s all. In most cases, there is no body passed to a **`DELETE`** call. Here’s the code for a sample **`DELETE`** call to the **`menu-items`** endpoint:

```jsx
const endpoint = 'http://127.0.0.1:8000/api/menu-items/17'
fetch(endpoint,
    {
        method: 'DELETE',
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json'
        }
    })
    .then(response => response.json())
    .then(data => {
        console.log(data)
    })
```

# ****Making authenticated calls with tokens****

If you want to make authenticated API calls using bearer tokens, pass the **`Authentication`** header in the second argument in the fetch function. Here is an authenticated **`POST`** call. Note how the bearer token is passed in the header section.

```jsx
const endpoint = 'http://127.0.0.1:8000/api/menu-items/17'
const token = “Some token”
fetch(endpoint,
    {
        method: 'POST',
        headers: {
            'Accept': 'application/json',
            'Content-Type': 'application/json',
            'Authentictation': 'Bearer ' + token
        },
        body: JSON.stringify(payload)
    })
    .then(response => response.json())
    .then(data => {
        console.log(data)
    })
```

You can do the same for **`GET`** calls as well.

# Conclusion

In this reading, you learned about making API calls in JavaScript using the native fetch function and how to process the response. You also learned how to send a JSON payload to make **`POST`**, **`PUT`** and **`PATCH`** calls.
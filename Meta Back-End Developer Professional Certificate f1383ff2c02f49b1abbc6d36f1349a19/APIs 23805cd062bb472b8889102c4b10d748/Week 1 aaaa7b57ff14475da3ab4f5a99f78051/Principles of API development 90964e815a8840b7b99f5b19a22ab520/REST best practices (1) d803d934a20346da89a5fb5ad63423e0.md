# REST best practices (1)

# Essential REST Best Practices

Creating a REST API is not just about writing code, it's about creating a well-designed architecture that is robust, reliable, and performs well under heavy loads. In this section, we'll outline the essential best practices that every API developer should know.

# ****KISS: Keep It Simple, Stupid****

The first and foremost principle of designing an API is to keep it simple and focused. **An API should be designed to perform a single task and perform it well, rather than trying to do too many things.** 

For example, consider the case of the Little Lemon project, where the manager wants to update the item of the day. 

A naive approach would be to let the API determine the previous item of the day, remove its status, **and then randomly pick one item based on some criteria** and set it as the new item of the day. But this approach is asking the API to do too many things and **might result in randomly picking an item that is not the most popular one.**

A better approach is to create two separate API endpoints, one to update the status of the previous item of the day and another to set the status of the new item of the day. 

For example, if the item of the day is item 16, the API to update its status would be **`menu-items/16`** with a HTTP PATCH or PUT request and the request body would have the status set to **`Off`**. The manager then manually selects a new item of the day and makes another API call to update its status. The API call would be **`menu-items/21`** with a HTTP PATCH or PUT request and the request body would have the status set to **`On`**.

```bash
PATCH /menu-items/16
{
  "status": "Off"
}

PATCH /menu-items/21
{
  "status": "On"
}
```

# Filtering, Ordering and Pagination

## Filtering and Ordering

When dealing with large result sets, it is always a good idea to provide a way to filter the results based on specific criteria. For example, the API **`/menu-items`** returns all available menu items at once, but a customer may only be interested in seeing the desserts or the main courses. Your API should be capable of filtering the results based on query string parameters.

```bash
GET /menu-items?type=desserts/
```

## Pagination

It's also important to provide a way to rearrange the results in ascending or descending order. By using pagination, you can deliver results in smaller chunks. For example, if the client application wants to display 20 menu items per page, it should not have to make an API call for all the items at once. The API request can specify the page number and the number of records per page.

```bash
GET /menu-items?page=10&per_page=4
```

# Versioning

When making changes to your API, there's always a risk of breaking a client's application. To avoid this, it's a good idea to use versioning for your API. There are several factors to consider when deciding if an updated version is needed or if a modification to an existing representation is enough. In general, you should only support two versions of any given resource, as maintaining multiple versions can be complex, error-prone, and costly.

```bash
GET /v1/menu-items
GET /v2/menu-items
```

# Caching

Caching is an essential best practice when it comes to RESTful APIs. **Implementing caching reduces the load on your database-related API calls and helps minimize the number of calls your client makes to your API.**

For example, if the mobile app makes a call to the endpoint **`menu-items`**, you can cache the results the first time it runs and then serve the cached result every time after that. This way, you can avoid putting a heavy load on your database every time you need to fetch **`menu-items`**. You will only update the cache when a menu item is modified or added.

For instance, if the **`appetizers`** menu was requested, but if there are no modifications to the menu items, all future calls to this endpoint can serve the same cached result without communicating with the database. This saves a lot of computing power.

To implement caching, it is important to send relevant HTTP headers in your response.

# Rate Limiting and Monitoring

To prevent abuse of your APIs, you can implement rate limiting. This limits the number of times someone can call your API in a period of time, like per minute, hour, or day. Some people even limit their APIs per 30 days.

In addition to rate limiting, monitoring is also important to ensure the best possible performance for your APIs. You should monitor latency to make sure your clients are getting the best possible response time.

It's important to keep an eye on HTTP status codes in the range of 400 to 499 and 500 to 599. Monitoring these status codes can help you identify any potential problems early on and assure that your API runs smoothly.

Monitoring network bandwidth is also important to know if someone is abusing your API. By keeping an eye on these metrics, you can maintain the health, performance, and sustainability of your API.

# Conclusion

By following these best practices and guidelines for creating sustainable APIs, you will be well on your way to designing great APIs.
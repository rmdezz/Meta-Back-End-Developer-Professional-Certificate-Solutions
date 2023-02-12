# Exercise: Know your tools

# Introduction

In this exercise, you are going to use the REST API client **Insomnia** to make HTTP Requests so make sure you’ve installed it on your computer. 

You will also use the Request and Response Service [httpbin.org](https://httpbin.org/). Httpbin.org is an open-source web service that allows you to make HTTP calls without any additional installations or dependencies.

You will be exploring the different functionalities available in Insomnia such as:

- Creating a **GET** request
- Creating a **POST** request with Form Data
- Creating a **POST** request with JSON Data

# Instructions

To get started, open **`Insomnia`** on your local device and navigate to the tab labeled **`DEBUG`.**

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled.png)

If you haven't installed Insomnia yet, you can download the install files at [https://insomnia.rest/](https://insomnia.rest/)

# Create a GET request

Open the [https://httpbin.org/](https://httpbin.org/) website and click on **HTTP Methods**. A menu with different HTTP methods will expand which you can add to your endpoints.

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%201.png)

### Step 1

In Insomnia, click on the **+** icon on the left-hand side of the screen and select **HTTP Request** from the drop-down menu.

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%202.png)

### Step 2

Double-click the request to change its title to **GET request using Insomnia**.

![Screenshot 2023-01-31 at 12.28.33 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.28.33_PM.png)

### Step 3

Click on the **GET** dropdown to see a list of available options and re-select **GET**.

Update the URL endpoint with the value: [https://httpbin.org/get](https://httpbin.org/get)

Press the **Send** button and notice the JSON output.

![Screenshot 2023-01-31 at 12.28.46 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.28.46_PM.png)

### Step 4

From the **Body** drop-down option, select **Multipart Form**.

![Screenshot 2023-01-31 at 12.29.43 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.29.43_PM.png)

Add the following values under **New name** and **New value**:

- New name: title
- New value: Lord of the Rings
    
    ![Screenshot 2023-01-31 at 12.32.51 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.32.51_PM.png)
    

Press the **Send** button once again and observe the changes.

![Screenshot 2023-01-31 at 12.33.01 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.33.01_PM.png)

Notice that the value of **`Content-Length`** has been updated to include the changes.

### Step 5

Update a form entry with the following details:

- New name: author
- New value: JRR Tolkien
    
    ![Screenshot 2023-01-31 at 12.33.21 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.33.21_PM.png)
    

Press the **Send** button once again. Notice that **Content-Length** has further been updated.

![Screenshot 2023-01-31 at 12.33.28 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.33.28_PM.png)

### Step 6

You can **Filter** your output using the Filter response body at the section in the bottom right-hand side of **Insomnia** as indicated in the screenshot below.

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%203.png)

Add the following filter inside it **(and press ENTER)**:

**`$.origin`**

![Screenshot 2023-01-31 at 12.34.19 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.34.19_PM.png)

It should update the **Preview**. The output will appear similar to what is displayed in the screenshot below.

![Screenshot 2023-01-31 at 12.35.00 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.35.00_PM.png)

### Step 7

Modify the filter incrementally as below which should produce the respective outputs.

```bash
$.headers
```

![Screenshot 2023-01-31 at 12.35.48 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.35.48_PM.png)

![Screenshot 2023-01-31 at 12.35.58 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.35.58_PM.png)

```bash
$.headers.Content-Type
```

![Screenshot 2023-01-31 at 12.36.55 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.36.55_PM.png)

![Screenshot 2023-01-31 at 12.37.06 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.37.06_PM.png)

**Note:** *The dot operator is used here to explore the contents of the JSON output. Also notice the value of the Content-Type is **form-data** because you selected Multipart form*.

Clear the contents of the **Filter response body**.

![Screenshot 2023-01-31 at 12.37.34 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.37.34_PM.png)

### Step 8

Now deselect the option for the name **title** and re-create the **GET** request.

![Screenshot 2023-01-31 at 12.38.20 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.38.20_PM.png)

![Screenshot 2023-01-31 at 12.38.27 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.38.27_PM.png)

![Screenshot 2023-01-31 at 12.38.38 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.38.38_PM.png)

Notice the change in the **`Content-Length`** again.

### Additional step

Now that you know the steps to create a **`GET`** request in **Insomnia**, you can explore different configuration settings by following the steps discussed to get more accustomed to the tool.

## Create a POST request with Form Data

### Step 1

Keeping the contents of the form data the same, update the request type to **POST** and update the URL endpoint to:

```bash
https://httpbin.org/post
```

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%204.png)

![Screenshot 2023-01-31 at 12.40.57 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.40.57_PM.png)

Press the **Send** button again. The output should appear as below:

![Screenshot 2023-01-31 at 12.41.15 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.41.15_PM.png)

Notice that the contents of the form are updated inside the output for the **`POST`** request.

### Step 2

Explore the other tabs under the output such as **`Headers`**, **`Cookies`** and **`Timeline`**.

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%205.png)

![Screenshot 2023-01-31 at 12.42.01 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.42.01_PM.png)

![Screenshot 2023-01-31 at 12.42.09 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.42.09_PM.png)

![Screenshot 2023-01-31 at 12.42.20 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.42.20_PM.png)

### Step 3

Since you have modified the same HTTP request, update the changes for the title of the request in the left-hand section to **POST request using Insomnia.**

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%206.png)

## ****Create a POST request with JSON Data****

### Step 1

Now further create another HTTP Request like the one at the beginning by pressing the **+** icon and selecting **HTTP Request**.

### Step 2

Update the request type to **POST** and the request label as:

```bash
**POST request using JSON object**
```

![Screenshot 2023-01-31 at 12.45.34 PM.png](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Screenshot_2023-01-31_at_12.45.34_PM.png)

**Note:** The labels are for reference and independent of the request type.

Paste the same URL endpoint that you used earlier in the URL **`text-box`**:

```bash
https://httpbin.org/post
```

The updated view should appear as below:

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%207.png)

### Step 3

Under the **Body** dropdown option, select JSON as the text input.

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%208.png)

A text input area should appear as below.

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%209.png)

### Step 4

Enter the following content inside the text input area:

```bash
{
  "title": "Lord of the Rings",
  "author": "JRR Tolkien",
  "published": {
    "year": 1954,
    "month": "July",
    "day": 29
  }
}
```

The output for the JSON input should appear as below:

![Untitled](Exercise%20Know%20your%20tools%201df531efa8164146a0e2e47327efcb73/Untitled%2010.png)

Notice the contents entered as JSON object in both the **data** and **json** field inside the JSON output.

### Step 5

- Add the following line to Filter response body:

```bash
$.json.published.year
```

The output will be as follows:

```bash
[
	1954
]
```

- Modify the **Filter response body** as follow:

```bash
$[json][published][day]
```

The output will be as follows:

```bash
[
	29
]
```

# Concluding Thoughts

There are several configuration options inside Insomnia. While using a REST API client it is good to explore these. You can also get help from other free and open-source API services that provide options to make API calls to access public data.
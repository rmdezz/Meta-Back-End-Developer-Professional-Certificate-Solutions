# Browser tools and extensions for API development

The browser's developer console is a useful tool for debugging API calls made from JavaScript on your website. Here's a step-by-step guide on how to use it:

## **Opening the Developer Console**

- In Chrome, you can open the developer console by pressing **`Control + Shift + I`** in Windows and Linux and **`Command + Option + I`** in MacOS.

## **Making an API Call**

- Go to the console tab and paste the following line of code to initiate a HTTP GET call to your API:

```bash
fetch('API_URL')
```

- Replace **`API_URL`** with any valid URL to test this.
- Go to the network tab and you'll see that the API call has been recorded.
- Click on the recorded call to see its details.
    
    ![Screenshot 2023-02-01 at 10.25.58 AM.png](Browser%20tools%20and%20extensions%20for%20API%20development%20ca968e1ae01d4e6482d44d1be7fece08/Screenshot_2023-02-01_at_10.25.58_AM.png)
    

## **Inspecting the API Call**

- In the details, you'll find the header and the preview tabs.
    
    ![Screenshot 2023-02-01 at 10.26.47 AM.png](Browser%20tools%20and%20extensions%20for%20API%20development%20ca968e1ae01d4e6482d44d1be7fece08/Screenshot_2023-02-01_at_10.26.47_AM.png)
    
- The header tab shows all the request-response headers involved in the API call.
    
    ![Screenshot 2023-02-01 at 10.27.16 AM.png](Browser%20tools%20and%20extensions%20for%20API%20development%20ca968e1ae01d4e6482d44d1be7fece08/Screenshot_2023-02-01_at_10.27.16_AM.png)
    
- The preview tab displays the output and the response tab shows the raw output of the API call.
    
    ![Screenshot 2023-02-01 at 10.27.32 AM.png](Browser%20tools%20and%20extensions%20for%20API%20development%20ca968e1ae01d4e6482d44d1be7fece08/Screenshot_2023-02-01_at_10.27.32_AM.png)
    
- The initiator tab shows the line in your JavaScript from where the API call was initiated.
    
    ![Screenshot 2023-02-01 at 10.27.49 AM.png](Browser%20tools%20and%20extensions%20for%20API%20development%20ca968e1ae01d4e6482d44d1be7fece08/Screenshot_2023-02-01_at_10.27.49_AM.png)
    
- Keep the **`Disable cache`** checkbox checked if you want to avoid caching and expect a fresh output from your APIs.
    
    ![Screenshot 2023-02-01 at 10.28.10 AM.png](Browser%20tools%20and%20extensions%20for%20API%20development%20ca968e1ae01d4e6482d44d1be7fece08/Screenshot_2023-02-01_at_10.28.10_AM.png)
    

## **Clearing the Recorded Calls**

- All the API calls from your JavaScript will be recorded in the network tab and you can inspect them one after another.
- You can also delete all the recorded calls by clicking on the **`Clear`** option.
    
    ![Screenshot 2023-02-01 at 10.28.29 AM.png](Browser%20tools%20and%20extensions%20for%20API%20development%20ca968e1ae01d4e6482d44d1be7fece08/Screenshot_2023-02-01_at_10.28.29_AM.png)
    

## **Formatting the JSON Output**

- Visit any API endpoint in your browser, for example, **`https://restcountries.com/v3.1/all`**.
- The JSON output might be messy and unformatted.
- To format the JSON output, install a JSON formatter extension from the Chrome extension store.
- After installing the extension, revisit the API endpoint and the output will be nicely formatted.

# Conclusion

With these steps, you'll be able to debug your API calls and understand how they're working with the help of the browser's developer console.
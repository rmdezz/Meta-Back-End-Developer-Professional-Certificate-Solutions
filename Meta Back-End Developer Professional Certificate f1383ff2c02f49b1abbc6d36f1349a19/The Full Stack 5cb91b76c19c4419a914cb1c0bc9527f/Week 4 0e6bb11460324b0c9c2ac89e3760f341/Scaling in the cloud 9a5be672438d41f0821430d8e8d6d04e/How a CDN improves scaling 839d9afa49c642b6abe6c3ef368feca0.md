# How a CDN improves scaling

# Introduction

Content Delivery Networks or CDNs are widely used to store static content files like HTML, CSS, JS, and images of web applications. CDNs deliver content from servers worldwide but always from the nearest server to the client, which has many advantages.

In this reading, you will learn how these CDNs work and what their benefits are.

# ****What is CDN****

A CDN has multiple servers which are called PoP or point of service and they run in different countries across the world. When you connect your web application to a CDN, each PoP can store a copy of the static files of your web application. For instance, when a visitor browses your application from Asia, the PoP closest to that visitor's ISP or internet service provider serves the application’s content.   Below is a diagram of a typical web application architecture without a CDN.

![Untitled](How%20a%20CDN%20improves%20scaling%20839d9afa49c642b6abe6c3ef368feca0/Untitled.png)

There are two significant benefits to this process of serving content via CDNs. **First, your web application visitors receive the content faster than those web applications that do not use CDNs.** And second, **your web application is not receiving direct traffic requesting those static files.** Thus, the load on the web server is reduced to a great extent.

# ****Push versus pull CDNs****

There are two types of CDN, push and pull CDNs. 

When your web application is connected to a push CDN you need to upload or push static files to the CDN every time you make changes to them. This can be done manually or automatically. But it requires extra effort from the application developer, and is therefore less popular.

On the other hand, a pull CDN updates files automatically. When visitors request a file, pull CDNs will check the origin server automatically to detect if the original static files have changed. 

**An origin server is a server you use to host your web application, and this is where the static files are stored.** If any changes are detected, the CDN server pulls those changed files and serves them. The new version of the files then also replaces the previous versions on the CDN. Since this is entirely automated, pull CDNs are used most often. Below is a diagram of how a pull CDN works.

![Untitled](How%20a%20CDN%20improves%20scaling%20839d9afa49c642b6abe6c3ef368feca0/Untitled%201.png)

# Advantages

The most significant benefit of using a CDN is the reduced delivery time for static files. When a web page renders, the static files take the longest to render. So, the faster they are served, the quicker the page will display.

Another benefit is the reduced workload on the web server. A web page can have hundreds of static CSS, JS, and image files linked to the page. For example, if there are **10** JavaScript files, **2** CSS files, and **60** image files, a single page visit will make **1+10+2+60=63** requests to the web server. If your webserver can serve **2000** requests per minute, with this calculation, it will be capable of serving only **2000/63 = 31** visitors per minute. Now, if you offload all the static files to a CDN, that means for every page visit, your webserver is getting only one request because other files are served directly from the CDN servers. The result is that your server can instantly serve **2000** visitors per minute! That's a massive improvement for little extra cost. With less load, the web server also works more efficiently.

Another benefit is that CDNs reduce the bandwidth from the webserver. CDNs come with huge uplink capacity and can serve a tremendous amount of data every second, which may not be possible to serve from a single web server with your current provider.

And lastly, it is beneficial to use images on the CDN. Many CDN automatically reduces image size or even convert them as they are requested to more modern formats like webp. Webp is a lossless format that preserves the quality of the image.

# Disadvantages

Sometimes, viewing the changed files delivered from the CDN may take time. This is because some CDNs take time to update the stored files with the newer versions. So, changes to any static file may not be instantly visible to your visitors. It may take **10** to **30** minutes or more due to different cache settings. But this rate varies significantly from provider to provider.

Another disadvantage is the bandwidth cost. When you deliver data from CDNs, the bandwidth cost will be higher than serving the files from your web server. And as your applications begin to grow, it can be costly.

Still, compared to the advantages CDNs offer, the disadvantages are far fewer and you should try to use a CDN whenever possible.

# Conclusion

In this reading, you learned more about content delivery networks or CDNs, the different types and how they enable web applications to scale up. You also learned about the pros and cons of using CDNs.
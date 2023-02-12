# Recap: What you know about client-server architecture

# Introduction

Full stack development includes both a back-end and front-end stack. The back-end, or the core of a web application or an API project, is hosted on a server or serverless platform. In turn, the web application or API is used by clients. So there are two distinct parts: a client and a server, and together they form the client-server architecture.

In this reading, you will learn more about client-server architecture.

# ****The client-server architecture****

Every website you browse, the multiplayer mobile games you play and modern home appliances connected to the internet – all of these are applications running on a client-server architecture.

- First is the client which is the computer or mobile device used to communicate with the back-end application. When the client devices only communicate with the back-end and just display or present the data and don’t apply the business logic, these devices are called thin clients. If client devices consume data from the API and do heavier data processing on the client side, they are called thick clients.
- Second is the server. In a client-server architecture, the server hosts the application's core that deals with incoming data, applies business logic and saves and processes data in a database. The application's core is hosted on cloud computing units, on virtual machines, containers, or a dedicated server. Using an N-tier architecture, the application can have different layers spread across multiple physical or virtual servers.

# How it works

In a client-server architecture, computers are connected via a network which can be either public or private. The client or the front-end application accepts the user data, does some basic validation, and sends the data to the server.

The server accepts the incoming data and runs through rigorous validation and sanitization processes to ensure the information is valid and doesn't contain any potentially malicious content. **Validation and sanitization are essential parts of every client-server architecture.** The rule of thumb is: don't trust anyone. **As the application developer, you must validate and sanitize data no matter how trusted the source of the data is.**

The data is then processed by business logic, saved or served from the database, and a response is sent back to the client. Then the client processes the server response data, makes decisions, or simply displays it to the visitor.

In a client-server architecture, the server should be capable of simultaneously handling multiple requests from multiple clients. **If the server capacity is insufficient and can’t accept the number of incoming requests then it has to be scaled.** **You can adjust the server capacity using different scaling techniques you will learn about later in this course.**

And, when it comes to communication, you should follow standard communication protocols like HTTP or Websocket to establish communication between the client and the server.

![Untitled](Recap%20What%20you%20know%20about%20client-server%20architectu%20711e76444a484e12af9ea7a0b6e79133/Untitled.png)

# Advantages

One of the most significant benefits of using client-server architecture is the separation of the different layers of your application. 

The database can be installed and managed in a totally separate layer, and the data stays synced in a centralized location. In this way it allows multiple clients to communicate and use that information at the same time.

Think about the Little Lemon application you have been working on throughout the courses in this program. Without client-server architecture, it wouldn’t be possible to host the restaurant data in a separate server and process it so that whenever something changes, every client sees the fresh and updated data.

Since different application parts are stored in different layers or tiers, scaling, optimizing, and securing the infrastructure and data becomes easier. Backing up and recovering data in case of accidental loss or hardware failure is also easier because you can directly deal with that tier or layer instead of potentially causing problems in the whole application.

Additionally, client-server architecture is cost-effective because you can host it on the cloud with an on-demand pricing model and pay only for what you use. You don't need to purchase expensive physical computers to host your application. You also don't need powerful clients to run the business logic. Everything is done on the server, and then the final output is served to the client, which they can display directly or after some minimal processing if required.

# Disadvantages

Like every architectural pattern, the client-server computing model also has some disadvantages. 

The first is management: you have to spend time configuring, managing, and maintaining the servers to keep them in working order. 

Also, unmonitored or abusive usage of the API provided by your application can cause a spike in monthly bills. Furthermore, security can be a big concern. **When a security breach occurs, sensitive user data can leak, and severe financial damage can follow. And, if the server goes down or becomes unresponsive for any reason, the client applications will also stop working.**

# Conclusion

This reading taught you about the very popular client-server architecture you can use in every full stack application or API project. You also learned about the advantages and disadvantages of client-server architecture.
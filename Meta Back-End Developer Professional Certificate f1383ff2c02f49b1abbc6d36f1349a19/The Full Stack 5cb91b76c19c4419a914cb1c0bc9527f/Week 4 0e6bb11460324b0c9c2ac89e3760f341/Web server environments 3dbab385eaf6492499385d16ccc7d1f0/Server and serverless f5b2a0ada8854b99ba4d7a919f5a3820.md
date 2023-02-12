# Server and serverless

# Introduction

- You now know about working with databases, writing backend applications using Django and creating APIs, as well as frontend applications.
- It's time to learn about deployment in server and serverless cloud computing.

# Deployment process

- To run a production application in the cloud, you need one or multiple servers to upload your application and link them to your domain.
- **This process of uploading code and data to the servers is called deployment.**
- Some people use manual deployment, while others use automated deployment.
- With the manual method, you need to manually upload everything using File Transfer Protocol (FTP), Secure File Transfer Protocol (SFTP), or tools like rsync.
- Automated deployments are easier when deployment is properly configured with a version control system and build tools.

# ****Continuous Integration and Continuous Deployment (CI/CD)****

- A typical workflow of CI/CD involves these steps:
    - Code
    - Version control
    - Build
    - Test
    - Deploy
- Tools that you can use for these steps are Jenkins, CircleCI, and GitHub's CI actions.
- If no test runner is involved, it's only continuous deployment.

# ****Hosting your Application****

- To host your code and database, you need to follow one of two approaches, server or serverless.
- Both methods require physical servers, but the deployment process makes them significantly different from each other and both have their advantages and disadvantages.

## Server approach

- Hosting companies sell two types of servers, dedicated and virtual servers.
- A dedicated server is a computing unit available for only your use.
- A virtual server is created using hypervisor software and a dedicated server is virtually split into multiple servers or virtual machines separate from each other.
- Advantages:
    - You can configure each virtual server with different operating systems and tools as they will not conflict with each other.
- Disadvantages:
    - You have to manage everything by yourself, which can be tedious and time-consuming.

## Serverless approach

- With a serverless approach, you don't have to configure anything, not for storage, CPU, or creating a production environment, and not even for memory allocation.
- Advantages:
    - Everything is properly managed by the serverless provider.
    - You don't manage or configure any servers and you don't have to worry about loads.
    - The serverless provider is closely integrated with the version control system and starts working automatically when you push code.
- Disadvantages:
    - Unmonitored consumption can cause a big spike in monthly bills.
    - When you use serverless providers, you are locked to the vendors' environment and conventions.
    - Moving apps to another vendor requires some code changes.

# Conclusion

- In this video, you learned about continuous integration and continuous deployment.
- You also learned how to host your application in the cloud using server or serverless technology.
- This knowledge will help you make your future apps available to the public or authorized people only.
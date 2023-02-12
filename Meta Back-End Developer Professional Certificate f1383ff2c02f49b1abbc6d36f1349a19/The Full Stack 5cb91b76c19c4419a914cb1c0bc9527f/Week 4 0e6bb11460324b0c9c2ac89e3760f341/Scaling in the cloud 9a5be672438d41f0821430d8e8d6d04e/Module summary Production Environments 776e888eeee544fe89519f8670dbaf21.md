# Module summary: Production Environments

# Introduction

Congratulations! You have completed this module on production environments and it's time to review the key concepts and elements you learned.

# Web server environments

- Deployment: The process of uploading code and data to servers, which can be manual or automated.
- Continuous Integration (CI): Imitates the production environment and runs tests.
- Continuous Deployment (CD): The uploading process.
- Hosting Applications:
    - Server: Dedicated server or virtual servers provide access to idle resources but must be managed manually.
    - Serverless: Everything is provided and managed by the serverless provider.

# Virtual machines and containerization

- Hypervisors:
    - Type 1: Directly works with hardware and runs fast but complex to set up.
    - Type 2: Works on top of an operating system, slower but does not require hardware setup.
- Resource Sharing:
    - Dedicated Server: Potentially wasteful but with no shared resources.
    - Virtual Machines: Shared resources, no wastage.
- Containerization: Packages applications and dependencies in container image files that can run anywhere regardless of operating system or hardware.
    - Pod: Group of connected containers sharing the same resource.
    - Node: Multiple pods related or working independently.
    - Container Orchestration: Management, deployment, networking, and scaling of the containers.

# PaaS, SaaS, DBaaS, and IaaS

- Platform as a Service (PaaS): Everything you need to run an application.
- Software as a Service (SaaS): Solves a specific problem and provides an API to use it.
- Database as a Service (DBaaS): Provides only database solutions.
- Infrastructure as a Service (IaaS): Creates infrastructure with servers.
- Self-hosted: Everything is hosted on your server and must be managed by you or your team.

# Cloud Computing

- Types of Cloud Infrastructure: Public, private, and hybrid cloud.
- Computing Unit: Virtual machines available for on-demand deployment.
- Storage: Available in gigabytes or terabytes or using object storage with an API.
- Database Solutions: Fully-managed solutions that scale automatically.
- Machine Learning: Requires a lot of computing power and is cheaper in the cloud.
- Networking in the Cloud: Can use public or private networking.
- Scaling in the Cloud:
    - Vertical Scaling: Adds RAM, CPU, or storage to a physical or virtual machine.
    - Horizontal Scaling: Adds nodes or virtual servers as the load goes up and removes nodes when they go down.
    - Auto-Scaling: Provided by cloud providers with no manual intervention or extra configuration needed.
- Load Balancing:
    - Load Balancing the Web Server: Can use round-robin or health-based approaches.
    - Load Balancing the Data Server: Can use horizontal scaling with clustering or master-slave replication.
    - Load Balancing the Cloud: Provided by cloud providers with internal load balancing.
- Content Delivery Network (CDN): Improves scaling by caching and serving static assets in the cloud. Determines the nearest point of presence (server where static assets are stored).

# Conclusions

You covered a lot of ground in this module and should be proud of your achievements! Take a break before diving into the final module.
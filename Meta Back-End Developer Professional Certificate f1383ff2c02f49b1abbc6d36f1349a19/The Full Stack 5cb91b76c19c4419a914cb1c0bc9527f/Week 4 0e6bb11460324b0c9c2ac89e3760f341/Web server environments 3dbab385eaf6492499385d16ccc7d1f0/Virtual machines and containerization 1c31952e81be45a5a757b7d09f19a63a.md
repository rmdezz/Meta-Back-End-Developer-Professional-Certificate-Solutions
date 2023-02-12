# Virtual machines and containerization

In this section, we will dive deeper into virtual servers and containers, two technologies used to host and run isolated applications.

# Virtual servers

A virtual server is created by splitting a dedicated server into multiple virtual machines (VMs) using hypervisor technology. There are two types of hypervisors involved in creating VMs:

- Type 1 hypervisor (also known as bare-metal hypervisor) is a software layer that works directly with server hardware and is more efficient in resource management. Examples of Type 1 hypervisors include KVM.
- Type 2 hypervisor works mostly on top of an operating system and is easier to manage than Type 1 hypervisors. Examples of Type 2 hypervisors include Oracle VirtualBox.

# Resource sharing in virtual servers

Virtual machines can be configured to use dedicated computing resources or share them. 

For example, a dedicated server with three terabytes of storage, 12 gigabytes of RAM, and six processing cores can provide its resources entirely to a single virtual machine or split them equally between multiple virtual machines. 

Dedicated resources ensure availability, **but they can also lead to wastage if they sit idle.** 

On the other hand, shared virtual machines can use the resources assigned to them, as well as extra resources from other shared machines when they are available.

# ****Containerization****

Containerization is a process of packing an application and its dependencies into a container image file, making it easier to run and manage. 

Container engines like Docker abstract the operating system layer, making containers smaller in size, faster, and more portable than virtual machines. It is recommended to keep containers lean by sticking to one process or application per container for efficient management.

## Key terms in containerization

- Pod: A group of tightly coupled containers that share the same resource and work together to solve a particular problem.
- Node: A physical or virtual machine that runs one or multiple pods.
- Cluster: Multiple pods and nodes that could be related or work independently.
- Container orchestration: The management, deployment, networking, and scaling of containers.

# Conclusion

In conclusion, this video has taught you about the different technologies used to host applications in the Cloud, including virtual servers and containers. You have also learned about key terms used in the world of containerization, including pods, nodes, clusters, and container orchestration. With this knowledge, you are now well equipped to successfully host your applications in the Cloud.
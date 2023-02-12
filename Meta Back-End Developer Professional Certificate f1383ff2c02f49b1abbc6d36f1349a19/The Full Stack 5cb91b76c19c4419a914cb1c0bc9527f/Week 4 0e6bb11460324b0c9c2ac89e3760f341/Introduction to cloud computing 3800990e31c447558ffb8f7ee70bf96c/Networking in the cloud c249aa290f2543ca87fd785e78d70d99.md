# Networking in the cloud

# Introduction

In this reading, you will learn about some exciting networking concepts used in cloud computing. You can use this knowledge to understand how servers communicate privately and publicly.

# ****Public versus private network****

In a public network, the cloud computing units are publicly accessible using IP addresses or URLs. 

On the other hand, computing units in a private network are not publicly accessible. These units are still accessible from the management console but don’t provide any public interface. To communicate publicly, the computing units can be on totally different networks. However, the units must be on the same network for private communication.

A load balancer sits in front of a typical infrastructure and is connected to multiple web servers. This load balancer will be connected to the public, but the web servers can connect to the load balancer both publicly and privately if they are on the same network.

# IP Address

An IP address is a communication protocol used in networks. This is a unique identifier to locate a machine or a device on the internet or on a private network. You can use one of the two popular IP addressing systems for this. The first one is the IP version 4 or [IPv4](https://en.wikipedia.org/wiki/Internet_Protocol_version_4) or simply IP4. The other one is [IPv6](https://en.wikipedia.org/wiki/IPv6) or IP6.

In the IPv4 system, the address is divided into four different parts, and each part can be numbers ranging from 0 to 255, separated by periods. So, the IPv4 address range is anything from **0.0.0.0 to 255.255.255.255**. The maximum length of an IPv4 address can be 15 characters. Here is a sample IPv4 address that belongs to Meta:

```jsx
69.63.176.13
```

In the IPv6 system, there are eight groups separated by a colon (:), and in each group, there are four hexadecimal digits. Facebook has adopted an IPv6 address:

```jsx
2a03:2880:2130:cf05:face:b00c:0:1
```

Did you notice the “face” and “b00c” in the IP address? They're both valid hexadecimal digits.

The IPv4 system can have a maximum of 4,294,967,296 unique IP addresses. There needs to be more in this growing modern world, and it can run out soon, which is why IPv6 was invented. You can have 3.4 x 1038 or 340 trillion, trillion, trillion unique addresses.

IPv6 is a new technology, and many countries worldwide are still adapting to IPv6.

When using IPv4, these ranges are used only in the private network, 1**0.0.0.0 — 10.255.255.255**; **172.16.0.0 — 172.31.255.255** and **192.168.0.0 — 192.168.255.255** so they are called private IP ranges.

One device or machine can have more than one IP address and both IPv4 and IPv6 addresses together.

# DNS System

Remembering IP addresses is tough. Imagine you host your application in a server that has a public IP address, but you access it using a domain or hostname. This is where DNS servers come in. DNS servers are public servers that store these domain names against their IP addresses. Whenever you request a URL starting with a domain name on your browser or a request, it goes to the DNS server, receives the IP address, and then connects to that machine.

# Bandwidth

Data that comes in or goes out from your server is called bandwidth. There are two types of bandwidths – incoming and outgoing. The data that comes to the server, for example, when you submit a form or upload files, is called incoming bandwidth or ingress bandwidth. And the data that leaves, for example, the webpage or API response or downloaded files, are counted as outgoing bandwidth or egress bandwidth.

# Uplink and downlink

In a server, uplink refers to the network or communication protocol used to send data outside the server. Similarly, the downlink is the network used to accept incoming data.

# ****Conclusion****

In this reading, you have learned the basic networking terms and how servers communicate with the public or other servers using IPv4 or IPv6 protocol. You also learned about egress and ingress bandwidth, uplink and downlink.
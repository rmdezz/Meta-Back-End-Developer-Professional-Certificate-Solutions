# Load balancing

Load balancers help to scale your application by distributing the load evenly among multiple nodes. In this video, we'll discuss different techniques used for load balancing.

# Load balancing the web server

The web server plays a crucial role in accepting HTTP requests and delivering the response to clients. Here are the two popular techniques used for load balancing the web server:

## **Round-Robin**

In this technique, the load balancer distributes the load equally among all the web servers. However, this technique may not work efficiently as not every request takes the same time to process.

## Health-based

This technique monitors the load on the web servers and distributes the load only on those nodes that are available and not already loaded.

# Reverse proxy

A reverse proxy can be used to perform load balancing. The reverse proxy can serve the static files and forward the application-specific URLs and API calls to the web server.

## CDN

Static files like HTML, CSS, JS, text files, and images can be offloaded to an external Content Delivery Network (CDN) to improve the performance of the web server. The CDN creates multiple copies of these files and serves them from the nearest data center.

# ****Load Balancing the Database****

Scaling a database is more complex than scaling a web server. Horizontal scaling is a better option than vertical scaling for sustainability. Here are two popular techniques used for scaling databases horizontally:

## **Sharding**

In this technique, a large database is split into multiple chunks and one database server holds one chunk.

## **Master-Slave Replication**

The whole database is replicated on multiple servers. One server acts as the master server where data modifications happen, and the other servers are slave servers. All read requests are evenly distributed among the slave servers.

# ****Managed Database Service****

Most cloud providers offer managed database services where they internally balance the loads and process a massive amount of data without causing any trouble or downtime. **This allows the developer to focus on development and business growth instead of managing the infrastructure.**

# ****Public and Private Load Balancing****

The techniques discussed so far are considered public load balancing, as they are directly dealing with external client requests. Private load balancing is sometimes necessary when heavily loaded internal, non-public applications or microservices communicate with each other over private IP addresses.

# Conclusion

In this video, you learned about various load balancing techniques for the web server and databases, as well as public and private load balancing.
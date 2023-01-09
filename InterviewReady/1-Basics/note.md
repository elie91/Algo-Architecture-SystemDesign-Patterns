# System Design

# Distributed System

1 - `Vertical Scaling` => Optimise process and increase the output with the same resource 

2 - `Preprocessing` => Preparing before at non pick hours (Cron Job)

3 - `Resilience` 
=> Keep Backups and avoid single point of failure (Master - Slave architecture)

4 - `Horizontal Scaling` => Add more resources

5 - `Micro services` => Separe resources and define their responsabilities 

6 - `Distributed System` , `Partitioning`=> Duplicate the system on a different place, communication between systems, route the request to the closest system to get quick responses

7 - `Load Balancing` 

8 - `Decoupling` 

9 - `Logging and metrics` => (Analytics, Auditing, Reporting, Machine Learning)

10 - `Extensibility` 



# Horizontal VS Vertical Scaling

Scalibility

1 - `Vertical Scaling` 
* Buy bigger machines
* `+` No load balancing required
* `-` Single point of failure if the machine down
* `+` Internal process communication (Fast)
* `+` Consistent
* `-` Hardware limit

2 - `Horizontal Scaling`

* Buy more machines
* `-` Load Balancing is required
* `+` Resilient, No single point of failure
* `-` Network calls between machines (RPC: Remote Protocol Communication) (Slow)
* `-` Data inconsistency
* `+` Scales as users increase

Initialy go for vertical, then as users increase, go to horizontal, with benefits of vertical (Consistency and internal process communication)

Considerations when designing a system
* Is it scalable
* Is it resilient
* Is it consistent

# Monolith VS Microservices

* `Monolith` 
  * All fonctionnalities of the app in one program
  * Can be horizontal scaled on multiple machines
  * `+` Less complex, good for small teams
  * `+` Less duplication
  * `+` Faster
  * `-` More context required
  * `-` Complicated Deployment
  * `-` Testing is complicated because code is not decoupled
  * `-` Single point of failure
  

* `Microservices` 
  * Fonctionalites are separated on different programs
  * Client talk to a API Gateway that redirect to the concerned service
  * `+` Scalibility
  * `+` Easier for new team member
  * `+` Working in parallel
  * `-` Need skilled architects
  
# Load Balancing

## Definition
Load balancing is the process of distributing network traffic across multiple servers or devices to ensure that no single device is overwhelmed by the traffic. 

The goal of load balancing is to maximize the throughput, minimize the response time, and avoid overloading any of the servers or devices in the system. This can be achieved by using load balancing algorithms that determine the best server or device to handle a request based on various factors such as the current load on the servers or devices, the capacity of the servers or devices, and the location of the client making the request. 

Load balancing can be performed at different layers of the network stack, such as at the network layer, transport layer, or application layer, depending on the requirements of the system.

## Algorithms

One example of a load balancing algorithm in JavaScript is a `round-robin` algorithm. A round-robin algorithm distributes requests in a cyclical manner, such that each server or device in the system receives an equal number of requests over time.

Here are a few more examples of load balancing algorithms:

* `Least connections`: This algorithm routes requests to the server or device with the fewest number of active connections. This can help to evenly distribute the load across the servers and reduce the risk of overloading any single server.

* `Weighted round-robin`: This algorithm is similar to the round-robin algorithm, but it allows you to assign weights to each server or device to indicate their relative capacity or capabilities. Requests are then distributed in proportion to the weights assigned to each server.

* `Least response time`: This algorithm routes requests to the server or device with the lowest average response time. This can help to ensure that requests are handled as efficiently as possible and that users experience the fastest possible response times.

* `IP hash`: This algorithm routes requests based on the hash value of the client's IP address. This can help to ensure that requests from the same client are always sent to the same server, which can be useful for maintaining session state or other client-specific data.

* `Random`: This algorithm randomly selects a server or device to handle each request. This can be useful in situations where the servers or devices have roughly the same capacity and there is no need to explicitly balance the load.


# Sharding

## Defintion

In a database, `sharding` is the process of storing data across multiple servers. It is a way of horizontally partitioning data in a database or search engine. Each individual partition is called a shard or database shard. Each shard is held on a separate database server instance, to spread load. Sharding is a horizontal scaling technique used to distribute data across multiple servers, and is often used to improve the performance and scalability of a system.

For example, a database that is used to store user data for a social media application might use sharding to store user data for different geographic regions on different servers. This would allow the database to handle a larger number of users and requests, since each server would only have to deal with a subset of the data.

Overall, sharding a database can help improve the performance and scalability of a system by distributing the data and load across multiple servers.

## Steps

There are several ways to shard a database, and the specific approach used will depend on the database system being used and the needs of the application. Here are some general steps that are involved in sharding a database:

1. Identify the data that needs to be sharded: The first step in sharding a database is to identify which data should be stored on which server. This typically involves dividing the data into logical partitions, such as by user ID or geographic region.

2. Choose a sharding key: A sharding key is a piece of data that is used to determine which shard a piece of data should be stored on. For example, in a social media application, the user ID might be used as the sharding key, since each user's data is likely to be stored on a different shard.

3. Set up the database servers: Once the data has been divided into shards and a sharding key has been chosen, the next step is to set up the database servers that will hold the shards. This typically involves installing and configuring the database software on each server.

4. Partition the data: The next step is to actually partition the data and store it on the appropriate servers. This typically involves writing code that processes the data and stores it on the correct server based on the sharding key.

5. Configure the application to use the sharded database: Finally, the application that uses the database will need to be modified to use the sharded database. This typically involves updating the database connection settings and adding code to handle routing requests to the correct database server based on the sharding key.

Overall, sharding a database involves dividing the data into logical partitions and setting up multiple database servers to store the data. The application that uses the database must also be updated to use the sharded database.

## Benefits

Sharding a database can offer several benefits, including:

1. `Improved performance`: By distributing the data and load across multiple servers, a sharded database can handle a larger number of requests and queries, which can improve the overall performance of the system.

2. `Improved scalability`: Sharding a database allows the system to scale horizontally, by adding more database servers as needed. This can be more cost-effective than scaling vertically, by using larger and more powerful servers.

3. `Improved availability`: By using multiple database servers, a sharded database can be more resilient to server failures. If one server goes down, the other servers can continue to handle requests and maintain availability.

4. `Improved security`: Sharding a database can help improve security by allowing the data to be distributed across multiple servers in different locations. This can make it more difficult for an attacker to compromise the entire database.

Overall, sharding a database can help improve the performance, scalability, availability, and security of a system by distributing the data and load across multiple servers.

## Issues

There are several potential issues that can arise when sharding a database:

1. `Complexity`: Sharding a database can be a complex process, especially if the database is large and has a lot of data. It can be challenging to divide the data into shards and configure the database servers to store the data.

2. `Performance`: In some cases, sharding a database can actually decrease performance, since queries that span multiple shards may be slower than queries against a single, unsharded database.

3. `Consistency`: When a database is sharded, it is possible for data to be inconsistent between shards. For example, if a user's data is stored on two different shards, and one shard is updated while the other is not, the data on the two shards will be out of sync. This can be mitigated by using techniques like eventual consistency or using a distributed database that supports transactions across shards.

4. `Increased hardware cost`: Sharding a database typically requires the use of multiple database servers, which can increase hardware costs.

5. `Increased development cost`: Sharding a database can also increase development costs, since the application and database must be modified to use the sharded database.

Overall, while sharding a database can help improve the performance and scalability of a system, it is not a solution that is appropriate for every situation. It is important to carefully evaluate the needs of the application and the potential trade-offs of sharding before deciding to implement it.



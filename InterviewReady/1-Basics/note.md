# System Design

# Table of contents
- [System Design](#system-design)
- [Table of contents](#table-of-contents)
- [Horizontal VS Vertical Scaling ](#horizontal-vs-vertical-scaling-)
  - [Vertical Scaling](#vertical-scaling)
  - [Horizontal Scaling](#horizontal-scaling)
- [Distributed System ](#distributed-system-)
- [Resilient System ](#resilient-system-)
- [Consistent System ](#consistent-system-)
- [Microservices ](#microservices-)
- [Monolith VS Microservices  ](#monolith-vs-microservices--)
  - [Monolith](#monolith)
  - [Microservices](#microservices)
- [Load Balancing ](#load-balancing-)
  - [Definition](#definition)
  - [Algorithms](#algorithms)
  - [Benefits](#benefits)
  - [Issues](#issues)
- [Sharding ](#sharding-)
  - [Defintion](#defintion)
  - [Steps](#steps)
  - [Benefits](#benefits-1)
  - [Issues](#issues-1)

# Horizontal VS Vertical Scaling <a name="horizontal-vs-vertical"></a>

`Scaling` is the process of increasing the capacity or performance of a system to meet increasing demand. There are two main approaches to scaling: horizontal scaling and vertical scaling.

`Horizontal scaling` involves adding more machines or servers to the system, each of which can handle a portion of the workload. This allows the system to scale out and handle more traffic or requests by distributing the workload across multiple machines. For example, if a website is receiving a lot of traffic, horizontal scaling could involve adding more web servers to the system to handle the increased traffic.

`Vertical scaling`, on the other hand, involves increasing the capacity of a single machine or server. This could involve adding more CPU, memory, or storage to the machine, or upgrading to a more powerful machine. Vertical scaling allows the system to scale up and handle more traffic or requests by increasing the capacity of a single machine.

## Vertical Scaling
* Buy bigger machines
* `+` No load balancing required
* `+` Internal process communication (Fast)
* `+` Consistent
* `-` Hardware limit
* `-` Single point of failure if the machine down

## Horizontal Scaling

* Buy more machines
* `+` Resilient, No single point of failure
* `+` Can scale more easily and quickly than vertical scaling
* `-` Load Balancing is required
* `-` Data inconsistency

Initialy go for vertical, then as users increase, go to horizontal, with benefits of vertical (Consistency and internal process communication)

Considerations when designing a system
* Is it scalable
* Is it resilient
* Is it consistent

# Distributed System <a name="distributed"></a>

A distributed system is a network of computers that work together to provide a single service or solve a common problem. In a distributed system, each computer in the network operates as a separate entity, and the system as a whole is designed to be decentralized, meaning that no single computer has complete control over the system.

There are several key characteristics of distributed systems, including:

* `Decentralization`: As mentioned, distributed systems are decentralized, meaning that no single computer has complete control over the system.

* `Concurrency`: Distributed systems are designed to allow multiple computers to work on a common task concurrently.

* `Scalability`: Distributed systems are often designed to be scalable, meaning that they can be easily expanded by adding more computers to the network as needed.

* `Fault tolerance`: Because distributed systems are decentralized, they are often more resistant to failures than centralized systems. If one computer in the network fails, the others can continue to operate and provide the service.

* `Transparency`: Distributed systems are designed to be transparent, meaning that users and applications should not be aware of the details of the system's underlying architecture.

Distributed systems are often used to provide services that require high availability, scalability, and performance, such as web services and cloud computing platforms.


# Resilient System <a name="resilient"></a>

A resilient system is a system that is able to withstand and recover from failures, disruptions, or other adverse conditions. Resilient systems are designed to be robust and flexible, and they are able to adapt to changing conditions and continue to function in the face of challenges.

There are several key characteristics of resilient systems, including:

* `Redundancy`: Resilient systems often incorporate redundant components or resources, which can take over if a primary component fails. This helps to ensure that the system can continue to function even if one or more components fail.

* `Fault tolerance`: Resilient systems are designed to be tolerant of faults or errors, and they are able to continue to operate even if some components are not functioning properly.

* `Scalability`: Resilient systems are often designed to be scalable, meaning that they can easily be expanded or contracted to meet changing demand.

* `Adaptability`: Resilient systems are able to adapt to changing conditions and continue to function effectively. This may involve the ability to reconfigure resources or change the way the system operates in response to changing conditions.

* `Monitoring and feedback`: Resilient systems often include monitoring and feedback mechanisms that allow them to detect problems and respond to them in a timely manner.

Resilient systems are important in a variety of contexts, including critical infrastructure, military operations, and commercial enterprises, where the ability to maintain operation in the face of adverse conditions is essential.

# Consistent System <a name="consistent"></a>

A consistent system is one that operates in a predictable and reliable manner, producing the same results for a given set of inputs regardless of when or how those inputs are provided.

A consistent system is focused on maintaining predictable and reliable behavior, even if this means sacrificing some level of flexibility or adaptability.

There are several concepts that can be applied when setting up a consistent system:

* ` Define clear requirements and constraints`: It is important to clearly define the requirements and constraints for the system in order to establish a consistent and predictable behavior. This includes defining input and output formats, as well as any rules or constraints that the system must follow.

* `Use consistent data structures`: Using consistent data structures, such as well-defined schemas or standardized APIs, can help to ensure that the system is able to process and handle data in a consistent manner.

* `Test and validate the system`: Testing and validating the system can help to identify and fix any inconsistencies or bugs that may impact the system's behavior.

* `Monitor and maintain the system`: Regular monitoring and maintenance of the system can help to identify and fix any issues that may arise over time, ensuring that the system remains consistent and reliable.

* `Use error handling and recovery mechanisms`: Implementing error handling and recovery mechanisms can help to ensure that the system is able to handle unexpected events or failures in a consistent and predictable manner, minimizing the impact of these events on the overall system.

* `Use version control and documentation`: Using version control and documentation can help to ensure that changes to the system are tracked and understood, which can help to maintain consistency over time.

# Microservices <a name="microservices"></a>

A microservices architecture is a type of distributed system.

In a microservices architecture, a system is broken down into a collection of smaller, independent services that communicate with each other over a network. Each service is designed to be self-contained and to perform a specific task or set of tasks, and the services are typically developed and deployed independently of each other.

Because a microservices architecture consists of multiple, independent services that communicate over a network, it is considered to be a type of distributed system. Like other distributed systems, microservices architectures are designed to be decentralized, scalable, and fault tolerant, and they often provide benefits such as increased flexibility and the ability to more easily evolve and update individual components of the system.

# Monolith VS Microservices  <a name="monolith-vs-microservices"></a>

## Monolith
  * All fonctionnalities of the app in one program
  * Can be horizontal scaled on multiple machines
  * `+` Less complex, good for small teams
  * `+` Less duplication
  * `+` Faster
  * `-` More context required
  * `-` Complicated Deployment
  * `-` Testing is complicated because code is not decoupled
  * `-` Single point of failure
  

## Microservices
  * Fonctionalites are separated on different programs
  * Client talk to a API Gateway that redirect to the concerned service
  * `+` Scalibility
  * `+` Easier for new team member
  * `+` Working in parallel
  * `-` Need skilled architects
  
# Load Balancing <a name="load-balancing"></a>

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

## Benefits

 It can have several benefits, including:

1. `Improved performance`: By distributing workloads across multiple resources, load balancing can help to reduce the strain on any single resource and improve the overall performance of the system.

2. `Increased reliability`: By using multiple resources to handle requests, load balancing can increase the overall reliability of the system. If one resource becomes unavailable, the workload can be shifted to other resources to ensure that the system remains operational.

3. `Better resource utilization`: Load balancing can help to ensure that all available resources are used efficiently, resulting in better resource utilization and potentially lower costs.

4. `Flexibility`: Load balancing can make it easier to scale a system up or down to meet changing demand, as workloads can be easily redistributed across resources.

5. `High availability`: Load balancing can help to ensure that a system remains available even if one or more of the underlying resources fail, as requests can be redirected to other resources.

## Issues

1. `Complexity`: Implementing load balancing can add complexity to a system, as it requires the use of additional software or hardware to distribute workloads and manage the allocation of resources.

2. `Overhead`: Load balancing introduces additional overhead, as it requires the use of additional resources to manage the distribution of workloads. This can result in reduced performance in some cases.

3. `Cost`: Depending on the scale of the system and the load balancing solution being used, the cost of implementing load balancing can be significant.

4. `Single points of failure`: If the load balancing solution itself becomes unavailable, it can create a single point of failure that affects the entire system.

5. `Compatibility issues`: In some cases, load balancing solutions may not be compatible with certain types of software or hardware, which can limit their use.

6. `Difficulty in monitoring and debugging`: Load balancing can make it more difficult to monitor and debug issues within a system, as requests may be distributed across multiple resources and it may be difficult to identify the source of problems.

# Sharding <a name="sharding"></a>

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



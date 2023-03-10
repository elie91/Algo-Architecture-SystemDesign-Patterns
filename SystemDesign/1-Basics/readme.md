
# Table of contents
- [Table of contents](#table-of-contents)
- [System Design](#system-design)
- [Horizontal VS Vertical Scaling](#horizontal-vs-vertical-scaling)
  - [Vertical Scaling](#vertical-scaling)
  - [Horizontal Scaling](#horizontal-scaling)
- [Distributed System](#distributed-system)
- [Resilient System](#resilient-system)
- [Consistent System](#consistent-system)
- [Reliable System](#reliable-system)
- [Master-Slave Architecture](#master-slave-architecture)
- [Microservices](#microservices)
- [Monolith VS Microservices](#monolith-vs-microservices)
  - [Monolith](#monolith)
  - [Microservices](#microservices-1)
- [Sharding](#sharding)
  - [Defintion](#defintion)
  - [Steps](#steps)
  - [Benefits](#benefits)
  - [Issues](#issues)


# System Design


System design is the process of defining the architecture, components, modules, interfaces, and data for a system to satisfy specified requirements. It is a broad and iterative process that involves a range of stakeholders, including users, business analysts, system architects, and engineers. The goal of system design is to develop a system that is cost-effective, maintainable, and scalable, while also meeting the needs of the users.

There are several steps involved in system design, including:

* `Requirements gathering`: Identifying and documenting the requirements of the system, including functional and non-functional requirements.
* `Conceptual design`: Creating a high-level design of the system, including the overall architecture and major components.
* `Logical design`: Defining the detailed functional and data requirements of the system.
* `Physical design`: Translating the logical design into a physical design, including selecting hardware and software components and specifying the interfaces between them.
* `Implementation`: Building the system according to the physical design.
* `Maintenance and evolution`: Continuously updating the system to meet changing requirements and address any issues that arise.
It is important to note that, system design is also can be done for non-IT systems, such as mechanical systems, electrical systems, and civil infrastructure systems etc.

In modern industry, a system design engineer, who is mainly responsible for designing systems and ensure the system will meet the requirement and perform the function it was intended for, the engineers who have skills in system design have a great impact on the industry and are sought-after

# Horizontal VS Vertical Scaling 

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

# Distributed System 

A distributed system is a network of computers that work together to provide a single service or solve a common problem. In a distributed system, each computer in the network operates as a separate entity, and the system as a whole is designed to be decentralized, meaning that no single computer has complete control over the system.

There are several key characteristics of distributed systems, including:

* `Decentralization`: As mentioned, distributed systems are decentralized, meaning that no single computer has complete control over the system.

* `Concurrency`: Distributed systems are designed to allow multiple computers to work on a common task concurrently.

* `Scalability`: Distributed systems are often designed to be scalable, meaning that they can be easily expanded by adding more computers to the network as needed.

* `Fault tolerance`: Because distributed systems are decentralized, they are often more resistant to failures than centralized systems. If one computer in the network fails, the others can continue to operate and provide the service.

* `Transparency`: Distributed systems are designed to be transparent, meaning that users and applications should not be aware of the details of the system's underlying architecture.

Distributed systems are often used to provide services that require high availability, scalability, and performance, such as web services and cloud computing platforms.


# Resilient System 

A resilient system is a system that is able to withstand and recover from failures, disruptions, or other adverse conditions. Resilient systems are designed to be robust and flexible, and they are able to adapt to changing conditions and continue to function in the face of challenges.

There are several key characteristics of resilient systems, including:

* `Redundancy`: Resilient systems often incorporate redundant components or resources, which can take over if a primary component fails. This helps to ensure that the system can continue to function even if one or more components fail.

* `Fault tolerance`: Resilient systems are designed to be tolerant of faults or errors, and they are able to continue to operate even if some components are not functioning properly.

* `Scalability`: Resilient systems are often designed to be scalable, meaning that they can easily be expanded or contracted to meet changing demand.

* `Adaptability`: Resilient systems are able to adapt to changing conditions and continue to function effectively. This may involve the ability to reconfigure resources or change the way the system operates in response to changing conditions.

* `Monitoring and feedback`: Resilient systems often include monitoring and feedback mechanisms that allow them to detect problems and respond to them in a timely manner.

Resilient systems are important in a variety of contexts, including critical infrastructure, military operations, and commercial enterprises, where the ability to maintain operation in the face of adverse conditions is essential.

# Consistent System

A consistent system is one that operates in a predictable and reliable manner, producing the same results for a given set of inputs regardless of when or how those inputs are provided.

A consistent system is focused on maintaining predictable and reliable behavior, even if this means sacrificing some level of flexibility or adaptability.

There are several concepts that can be applied when setting up a consistent system:

* ` Define clear requirements and constraints`: It is important to clearly define the requirements and constraints for the system in order to establish a consistent and predictable behavior. This includes defining input and output formats, as well as any rules or constraints that the system must follow.

* `Use consistent data structures`: Using consistent data structures, such as well-defined schemas or standardized APIs, can help to ensure that the system is able to process and handle data in a consistent manner.

* `Test and validate the system`: Testing and validating the system can help to identify and fix any inconsistencies or bugs that may impact the system's behavior.

* `Monitor and maintain the system`: Regular monitoring and maintenance of the system can help to identify and fix any issues that may arise over time, ensuring that the system remains consistent and reliable.

* `Use error handling and recovery mechanisms`: Implementing error handling and recovery mechanisms can help to ensure that the system is able to handle unexpected events or failures in a consistent and predictable manner, minimizing the impact of these events on the overall system.

* `Use version control and documentation`: Using version control and documentation can help to ensure that changes to the system are tracked and understood, which can help to maintain consistency over time.

# Reliable System 

In the context of systems design, a reliable system is one that can be trusted to perform its intended functions correctly and consistently. A reliable system should be able to handle a variety of inputs and workloads, and should produce accurate and consistent results. It should also be able to withstand failures or disruptions, and should be able to recover from them in a controlled and predictable manner.

There are several factors that can contribute to the reliability of a system, including:

* `Robust design`: A well-designed system is more likely to be reliable, as it will be able to handle a variety of inputs and workloads without breaking down or producing incorrect results.

* `High quality components`: Using high quality components can help to ensure that the system is less likely to fail or produce incorrect results.

* `Error handling and recovery mechanisms`: Implementing error handling and recovery mechanisms can help to ensure that the system is able to handle failures or disruptions in a controlled and predictable manner, minimizing the impact on the overall system.

* `Testing and validation`: Thoroughly testing and validating the system can help to identify and fix any issues that could impact its reliability.

* `Regular maintenance`: Regular maintenance and monitoring of the system can help to identify and fix any issues that may arise over time, helping to maintain its reliability.

Reliability is an important property of any system, as it allows users to trust the system and have confidence in its results. Ensuring the reliability of a system is an important consideration in systems design.

`Reliability` and `consistency` are similar, but not identical, concepts. In the context of systems design, reliability refers to the ability of a system to perform its intended functions correctly and consistently over time. A reliable system should be able to handle a variety of inputs and workloads, and should produce accurate and consistent results. It should also be able to withstand failures or disruptions, and should be able to recover from them in a controlled and predictable manner.

Consistency, on the other hand, refers to the predictability and uniformity of a system's behavior. A consistent system is one that produces the same results for a given set of inputs, regardless of when or how those inputs are provided. 

Consistency is an important property of any system, as it allows users to trust the system and have confidence in its results.

While consistency is a key factor in determining the reliability of a system, it is not the only factor. A system can be consistent, but not necessarily reliable, if it produces incorrect or inconsistent results. On the other hand, a reliable system should also be consistent, as it should produce the same results for a given set of inputs.

# Master-Slave Architecture 

In a master-slave architecture, one machine or server (the master) is responsible for controlling and coordinating the work of one or more other machines or servers (the slaves). The master and slave systems are typically connected in a network, and the slaves are responsible for executing tasks and processing data as directed by the master.

One common use case for a master-slave architecture is in `distributed systems`, where the master is responsible for distributing tasks or data to the slaves for processing. The slaves then execute the tasks and return the results to the master, which can then aggregate the results and provide them to the client.

Master-slave architectures can provide several benefits, including:

* `Improved performance`: By distributing the workload across multiple machines, a master-slave architecture can improve the overall performance of the system.

* `High availability`: If one of the slaves fails, the master can redirect the workload to another slave, helping to ensure that the system remains available and operational.

* `Ease of management`: The master can be used to manage and coordinate the work of the slaves, which can make the overall system easier to manage.

However, there are also some potential drawbacks to using a master-slave architecture. For example, the system may be more vulnerable to failure if the master machine goes down, and it can be more complex to design and manage a system with multiple machines.


# Microservices 

A microservices architecture is a type of distributed system.

In a microservices architecture, a system is broken down into a collection of smaller, independent services that communicate with each other over a network. Each service is designed to be self-contained and to perform a specific task or set of tasks, and the services are typically developed and deployed independently of each other.

Because a microservices architecture consists of multiple, independent services that communicate over a network, it is considered to be a type of distributed system. Like other distributed systems, microservices architectures are designed to be decentralized, scalable, and fault tolerant, and they often provide benefits such as increased flexibility and the ability to more easily evolve and update individual components of the system.

# Monolith VS Microservices 

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



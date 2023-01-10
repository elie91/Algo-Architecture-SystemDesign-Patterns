
# Table of contents
- [Table of contents](#table-of-contents)
- [Gateway](#gateway)
  - [Definition](#definition)
  - [Vs Load balancer](#vs-load-balancer)
  - [In Microservices](#in-microservices)
- [Reverse Proxy](#reverse-proxy)


# Gateway

## Definition

In software architecture, a `gateway` is a component that acts as an entry point for external requests to a system or service. It can be thought of as a reverse proxy that sits in front of one or more back-end services and forwards incoming requests to the appropriate service. The gateway can also perform other functions, such as authentication, rate limiting, caching, and request/response transformation.

A gateway is typically used to provide a single point of entry to a complex system, and to abstract away the underlying details of the system's architecture from the client. This allows the system to evolve and scale independently of the client, and also provides a way to add new features and capabilities to the system without impacting existing clients.

A `API Gateway` is a specific type of Gateway, focused on managing and proxy API calls, such as services in microservices architecture, where API calls are the entry point and API Gateway would be the first layer between client and services.

Some of the main benefits of using a gateway include:

* `Improved security`, as all external requests pass through a single point of control that can be configured to enforce security policies.
* `Increased flexibility`, as the gateway can route requests to different back-end services based on various criteria, such as the URL or headers of the request.
* `Improved scalability`, as the gateway can distribute incoming requests across multiple back-end services to balance load.
* `Improved maintainability`, as changes to the system's architecture can be made behind the gateway without impacting clients.

## Vs Load balancer

An API Gateway can perform some of the functions of a load balancer, but they are not the same thing.

A load balancer is a component that `distributes incoming network traffic across multiple servers` to ensure that no single server is overwhelmed with too much traffic. The goal of a load balancer is to increase the availability and scalability of a system by distributing load across multiple servers.

An API Gateway, on the other hand, is a component that sits between external clients and a set of back-end services. Its main function is to `act as an entry point for incoming requests`, and to forward those requests to the appropriate back-end service.

An API Gateway can also perform other functions such as:

* Security : handling security requirements like authentication and authorization
* Translation: translate incoming request to the target service format
* Caching : caching commonly-used data to reduce the number of requests to the backend services.
* 
However, an API Gateway can also include load balancing capabilities, in order to distribute the incoming requests to multiple back-end services based on certain criteria such as the URL of the request or the amount of load on the service.

In a `microservices` architecture, it's common to have both an API Gateway and a Load Balancer. The API Gateway acts as a single entry point for external clients, while the load balancer distributes incoming requests to multiple instances of a microservice to ensure that it can handle the traffic.

So, while an API Gateway and a Load Balancer can both perform routing and forwarding of requests, they have different primary focus, and are not mutually exclusive components

## In Microservices

In a microservices architecture, the API Gateway and load balancer are typically placed at the edge of the network, closest to the external clients. This allows them to handle incoming requests before they reach the internal network and microservices.

The API Gateway is responsible for receiving incoming requests from external clients and forwarding them to the appropriate microservice. It can also perform other functions such as authentication, rate limiting, request/response transformation, and caching.

The load balancer, on the other hand, is responsible for distributing incoming requests to multiple instances of a microservice to ensure that the service can handle the traffic.

Here's a general architecture diagram:

[External Clients] -> [API Gateway] -> [Load Balancer] -> [Microservices]

In this scenario, external clients make requests to the API Gateway, which acts as a single entry point for all requests. The API Gateway then forwards the request to the load balancer, which distributes the request to one of the available instances of the targeted microservice. The microservice then processes the request and returns a response, which is sent back to the client through the API Gateway and Load balancer.

It's worth mentioning that in some cases, depending on the specific requirements and constraints of the system, it's possible to have the API Gateway and Load Balancer integrated into a single component, and also other network components like firewall, security rules and monitoring, might be added to this architecture.


# Reverse Proxy

A `reverse proxy` is a type of proxy server that sits in front of one or more web servers and forwards incoming requests to the appropriate server. The name "reverse proxy" comes from the fact that it sits in front of the web server and proxy requests in the opposite direction, as opposed to a forward proxy, which sits in front of the client and proxy requests towards the server.

Reverse proxies have several benefits:

* Security: A reverse proxy can act as a barrier between the internal network and the Internet, protecting web servers from direct attack by filtering incoming requests and hiding the identity and characteristics of the web servers.
* Load balancing: A reverse proxy can distribute incoming requests across multiple web servers to balance the load and improve performance.
* Caching: A reverse proxy can cache commonly-used content, reducing the number of requests that need to be forwarded to the web servers.
* SSL termination: A reverse proxy can handle SSL encryption and decryption, freeing the web servers from the computational burden of performing these tasks.
* Compression: A reverse proxy can compress content before it is sent to the client, reducing the amount of data that needs to be transmitted and improving load times.
  
Reverse proxies are often used in conjunction with other software such as firewalls, load balancers, and content delivery networks (CDNs) to build a robust and scalable infrastructure that can handle high traffic and security threats.

It's important to mention that a reverse proxy can work as an API Gateway as well, as it sits in front of multiple services and forward requests to the appropriate one, being able to perform same functions (Security, Load balancing, Caching, etc) as an API Gateway do.
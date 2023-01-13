
# Table of contents
- [Table of contents](#table-of-contents)
- [Load Balancing](#load-balancing)
  - [Definition](#definition)
  - [Algorithms](#algorithms)
  - [Benefits](#benefits)
  - [Issues](#issues)
- [Gateway](#gateway)
  - [Definition](#definition-1)
  - [Vs Load balancer](#vs-load-balancer)
  - [In Microservices](#in-microservices)
- [Reverse Proxy](#reverse-proxy)
- [SSL](#ssl)
- [TLS](#tls)
- [SSL Caching](#ssl-caching)
- [Cloudfare](#cloudfare)
- [CDN](#cdn)
- [DDOS Attack](#ddos-attack)
- [Rate limiting](#rate-limiting)
  - [Pros](#pros)
  - [Cons](#cons)
- [Web Application Firewall (WAF)](#web-application-firewall-waf)
  - [Pros](#pros-1)
  - [Cons](#cons-1)


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

* `Security`: A reverse proxy can act as a barrier between the internal network and the Internet, protecting web servers from direct attack by filtering incoming requests and hiding the identity and characteristics of the web servers.
* `Load balancing`: A reverse proxy can distribute incoming requests across multiple web servers to balance the load and improve performance.
* `Caching`: A reverse proxy can cache commonly-used content, reducing the number of requests that need to be forwarded to the web servers.
* `SSL termination`: A reverse proxy can handle SSL encryption and decryption, freeing the web servers from the computational burden of performing these tasks.
* `Compression`: A reverse proxy can compress content before it is sent to the client, reducing the amount of data that needs to be transmitted and improving load times.
  
Reverse proxies are often used in conjunction with other software such as firewalls, load balancers, and content delivery networks (CDNs) to build a robust and scalable infrastructure that can handle high traffic and security threats.

It's important to mention that a reverse proxy can work as an API Gateway as well, as it sits in front of multiple services and forward requests to the appropriate one, being able to perform same functions (Security, Load balancing, Caching, etc) as an API Gateway do.

# SSL

`Secure Sockets Layer` (SSL) is a security protocol that was widely used to establish an encrypted link between a web server and a web client (browser). The protocol is designed to ensure the secure and private transmission of sensitive information, such as credit card numbers or personal information, over the internet.

When a client (e.g. a browser) connects to a server using SSL, the client and server perform a "handshake" to establish a secure connection. During the SSL handshake, the client and server agree on a common encryption standard to use for the session, authenticate each other's SSL certificates, and establish session keys to encrypt the data that will be exchanged during the session.

The SSL protocol was succeeded by `Transport Layer Security` (TLS) protocol, which is a more recent and more secure version of SSL. TLS is now widely used to establish secure connections on the web.

In summary, SSL/TLS is a security protocol that enables secure and private communication over the internet, it is used to encrypt the data sent between a client (e.g. web browser) and a server (e.g. website) to ensure that the information is kept private and secure, and to verify the identity of the website being accessed.


# TLS

`Transport Layer Security` (TLS) is a security protocol that provides privacy and data integrity between communicating applications and their users on the Internet. It is the successor to the Secure Sockets Layer (SSL) protocol and is designed to provide secure communication over the internet.

TLS works by establishing an encrypted link between a client (e.g. a web browser) and a server (e.g. a website) using a process called a "handshake." During the handshake, the client and server agree on a common encryption standard to use for the session, authenticate each other's certificates, and establish session keys to encrypt the data that will be exchanged during the session.

TLS is used to secure a wide variety of internet protocols, such as HTTP (to secure web traffic), SMTP (to secure email), and FTP (to secure file transfers). It is also used to secure other internet protocols, like voice over IP (VoIP), instant messaging (IM) and virtual private networks (VPNs).

TLS is designed to provide confidentiality, integrity, and authenticity of data in communication. It provides confidentiality by encrypting the data, integrity by checking data for tampering and authenticity by authenticating the identity of the communicating parties.

In summary, TLS is a security protocol that provides secure communication over the internet by encrypting the data sent between a client and a server, it is used to ensure the privacy and integrity of the data and to authenticate the identity of the communicating parties. It is the successor of SSL and is the most widely used protocol to secure internet communication.


# SSL Caching

In software architecture, `SSL caching` refers to the process of temporarily storing `SSL` (Secure Sockets Layer) and `TLS` (Transport Layer Security) certificates in a cache to speed up the SSL/TLS negotiation process. Caching these certificates allows the server to quickly retrieve them and complete the SSL/TLS handshakes with clients without having to look them up in a certificate store every time. This can improve the performance and scalability of the server by reducing the number of SSL/TLS negotiations that need to take place.

# Cloudfare
There are several benefits for a company to use Cloudflare:

* Improved Performance: Cloudflare can significantly improve website performance by caching content at its global network of data centers, reducing the load on the origin servers, and delivering content to users more quickly.

* DDoS Protection: Cloudflare provides built-in DDoS protection that can help to protect against large-scale DDoS attacks, which can overwhelm a website and cause it to become unavailable.

* Security: Cloudflare offers several security features such as Web Application Firewall (WAF), that can help to protect a website from common web-based attacks like SQL injection and cross-site scripting (XSS).

* Content Delivery Network (CDN): Cloudflare's global network of data centers also functions as a CDN, which can help to improve website performance by caching and delivering content to users from the closest data center.

* Cost savings: Cloudflare offers a variety of pricing plans, including a free plan that can help small businesses and individual website owners to improve the performance and security of their websites without incurring significant costs.

* Easy to use: Cloudflare is easy to set up and manage, with a user-friendly interface and a variety of tools for monitoring and troubleshooting issues.

* Analytics: Cloudflare offers analytics that provides insights about website traffic, such as the number of requests, the geographic location of visitors, and the types of devices used to access the site.

* Customizable: Cloudflare allows for customizing rules and settings to suit the specific needs of a website, such as blocking certain countries or IP addresses, redirecting traffic, and more.

# CDN

A `Content Delivery Network` (CDN) is a network of servers that are distributed across multiple geographic locations. The main purpose of a CDN is to deliver content to users from the server that is closest to them, in order to reduce latency and improve the performance of the website.

When a user requests a web page or other content, the CDN will redirect the request to the server that is closest to the user. This is done by routing the request through the CDN's network of servers, which are strategically placed in different locations around the world.

CDN's can help to:

* Reduce the load on a single server
* Improve the speed and performance of a website by reducing the distance that data has to travel
* Increase the availability and reliability of a website by routing traffic around any issues that might occur on a single server
* Protect against DDoS attack
* Provide a caching mechanism for frequently requested content, reducing the need to retrieve it from the origin server each time.

In summary, CDNs are used to distribute the content of a website across multiple servers in different locations, so that users can access it faster and more reliably.

# DDOS Attack

DDoS stands for `Distributed Denial of Service`. It is a type of cyber attack that aims to make a website or online service unavailable to users by overwhelming it with a large amount of traffic from multiple sources.

In a DDoS attack, the attacker uses a network of infected computers, also known as a botnet, to flood the targeted website or service with a large amount of traffic. This traffic can come from multiple sources, such as computers, servers, or even Internet of Things (IoT) devices that have been infected with malware.

The goal of the attack is to overwhelm the targeted website or service with more traffic than it can handle, causing it to slow down or become unavailable. This can be accomplished by sending large volumes of traffic, using a large number of connections, or by using specific types of traffic that are designed to take advantage of vulnerabilities in the targeted website or service.

DDoS attacks can cause serious damage to a business, as it can make their website or service unavailable to customers and cause financial loss. Additionally, it can damage the reputation of the company, as customers may lose trust in the company if they can't access their services.

To protect against DDoS attacks, companies can use a combination of techniques, such as using a CDN, implementing rate limiting, and using firewalls and intrusion detection and prevention systems (IDS/IPS). Additionally, they can also use specialized DDoS protection services that can detect and block DDoS traffic before it reaches the targeted website or service.


# Rate limiting

 Impose a limit on the number of requests that can be made to the origin servers in a given time period. This will prevent a single attacker from overwhelming the servers with too many requests.

 To set up rate limiting in a Node.js application, you can use a middleware library such as express-rate-limit. Here is an example of how to use it in an express.js application:

 ```javascript
const rateLimit = require("express-rate-limit");
const app = express();

const limiter = rateLimit({
  windowMs: 15 * 60 * 1000, // 15 minutes
  max: 100, // limit each IP to 100 requests per windowMs
  message: "Too many requests, please try again later"
});

//  apply to all requests
app.use(limiter);

// apply to one request
app.use("/api/", limiter);
 ```

## Pros

* Protection against DDoS attacks: Rate limiting can help to protect against DDoS attacks by limiting the number of requests that a single IP address can make in a given time period.

* Improved performance: By limiting the number of requests that can be made to the server, rate limiting can help to improve overall website performance by reducing the load on the server.

* Easy to implement: Rate limiting can be easily implemented using middleware libraries such as express-rate-limit.

## Cons

* False positives: In some cases, legitimate users might be blocked due to the rate limiting rules.

* Bypass: Some attackers may use multiple IPs to bypass the rate limiting, this is known as IP spoofing.

* Limited effectiveness: Rate limiting can only be effective if the number of requests is lower than the limit, it might not be effective if the number of requests is extremely high, in that case, other measures like DDoS protection service should be used.

* Additional load: rate limiting might add additional load on the server as it needs to track the number of requests made by each IP address, this might increase the CPU and memory usage.

It's worth noting that rate limiting is just one of the many measures that can be used to protect a website from DDoS attacks, and it should be used in conjunction with other security measures such as a WAF, CDN and DDoS protection service.


# Web Application Firewall (WAF)

A Web Application Firewall (WAF) is a security system that is placed in front of a web application to protect it from common web-based attacks such as SQL injection, cross-site scripting (XSS), and others.

Here are the steps to set up a WAF for your website:

* Sign up for a WAF service: There are many WAF providers available, such as Cloudflare, AWS WAF, and Azure WAF. Each provider offers different features, pricing, and coverage, so it's important to choose one that fits your needs.

* Configure your WAF: Once you have signed up for a WAF service, you will need to configure it by adding your website's domain name and setting up the appropriate DNS settings. Depending on the provider, you may also need to configure other settings, such as security rules, IP blocking and allowlisting, and origin servers.

* Update your website's code: To use a WAF, you will need to update your website's code to reference the WAF's URL instead of your origin server's URL. This can be done by modifying the HTML, CSS, and JavaScript files, or by using a global WAF URL in your web application.

* Test and monitor: Once your WAF is set up, it's important to test your website's security and monitor it to ensure that it's working as expected. This can be done using tools like Google Analytics and other analytics platforms provided by WAF providers.

## Pros

* Improved security: WAF can help to protect a website from common web-based attacks such as SQL injection, XSS, and others, by analyzing and blocking malicious traffic before it reaches the origin servers.

* Customizable: Most of the WAF providers allows to customize rules and settings to suit the specific needs of a website, such as blocking certain countries or IP addresses, redirecting traffic, and more.

* Scalability: WAF providers have a large number of servers distributed across multiple locations, which can help to distribute the load across multiple servers and improve scalability.

## Cons

* Additional cost: Using a WAF service can be an additional cost for a website, especially if you have a high amount of traffic or a large number of files that need to be cached.

* Limited control: Depending on the provider, you may have limited control over the security rules, IP blocking, and origin servers.

* Complexity: Setting up and managing a WAF can be complex, especially for large and dynamic websites, it requires proper planning and testing to ensure that it is working as expected.

* False positives: In some cases, legitimate traffic may be blocked by the WAF, this can be solved by fine-tuning the rules and settings or by using a more sophisticated WAF.

It's worth noting that using a WAF is just one of the many measures that can be used to improve website security, and it should be used in conjunction with other security measures such as rate limiting, caching, CDN, and DDoS protection service


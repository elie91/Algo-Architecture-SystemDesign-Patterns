

# Table of contents
- [Table of contents](#table-of-contents)
- [Hexagonal Architecture](#hexagonal-architecture)
  - [Definition](#definition)
  - [In distributed system](#in-distributed-system)
  - [Compared to Microservices](#compared-to-microservices)
- [Dependency Injection](#dependency-injection)
- [Inversion Of Controls](#inversion-of-controls)


# Hexagonal Architecture 

## Definition
Hexagonal architecture, also known as the `Ports and Adapters` architecture, is a software design pattern that aims to separate the concerns of different parts of an application, making it more flexible and easier to maintain. It was first introduced by Alistair Cockburn in his 2005 book "Writing Effective Use Cases."

The key idea behind hexagonal architecture is to structure the application around a central domain model, which represents the core business logic of the system. This model is surrounded by a set of interfaces, called "ports," which define how the model can be interacted with. The ports are then implemented by a set of adapters, which provide the actual implementation of the interactions.

The architecture is hexagonal because the ports and adapters form a hexagon around the core domain model, and this hexagon shape is used to illustrate the separation of concerns and the interactions between the different parts of the system.

One of the key advantages of this architecture is that it allows you to change the implementation of a particular port without affecting the rest of the system. For example, if you wanted to change the persistence mechanism for your application from a relational database to a NoSQL database, you could do so by replacing the database adapter with a new adapter that implements the same port, without having to change the domain model or any of the other adapters.

Hexagonal architecture also promotes the use of `dependency injection`, which allows you to easily swap out different implementations of ports and adapters during testing. This makes it easier to write automated tests for your application, since you can test the domain model in isolation, by injecting fake implementations of the ports and adapters.

In short, Hexagonal Architecture is a software architecture pattern that:

* aims to separate the concerns of the different parts of an application
* focuses on the core business logic and keep it isolated
* allow easy modification of the implementation of certain parts of the application
* promotes the use of dependency injection.

## In distributed system

Hexagonal architecture, also known as "ports and adapters" or "onion architecture," is a software design pattern that is used to structure the components of a software system in a way that separates the concerns of the application's external dependencies from its core functionality. This allows the application to be more easily tested and maintained, and makes it more resilient to changes in its external environment.

While hexagonal architecture is not specifically tied to distributed systems, it can be used as part of the design of a distributed system. In a distributed system, the core functionality of an application is typically spread across multiple systems or devices, and communication between these systems can be complex. By using hexagonal architecture, the external dependencies of each system or device can be clearly defined and managed, making it easier to handle communication and coordination between the different parts of the system. Additionally, hexagonal architecture can make it easier to add or remove systems or devices from the system, and can help to ensure that the system as a whole is more robust and fault-tolerant.

It's worth noting that hexagonal architecture is not a solution for all problems, there are scenarios where other architectures like microservices or event-driven architecture could be more appropriate. But it is a solid design pattern that can make the application more loosely coupled and independent from the infrastructure, making it a good fit for the distributed systems.

## Compared to Microservices

Hexagonal architecture and microservices architecture are both software design patterns, but they address different concerns and are used in different contexts.

Hexagonal architecture is a pattern for structuring the components of a software system in a way that separates the concerns of the application's external dependencies from its core functionality. This makes the application more easily tested and maintained, and helps to ensure that it is more resilient to changes in its external environment.

On the other hand, microservices architecture is a way of designing a system by breaking it down into a set of independent, autonomous services that communicate with each other over well-defined interfaces. Each service is responsible for a specific business capability, and is designed to be small, focused, and easy to deploy, test, and scale.

While microservices architecture is primarily focused on the decomposition of a system into smaller, independently deployable services and how they communicate with each other, Hexagonal Architecture is focused on separating the application from its dependencies, so they can be easily replaced, tested or mocked out.

That said, there is some overlap between the two patterns, and they can be used together in a single system. For example, a microservices architecture can use hexagonal architecture to structure the components of each individual service, which will allow them to be more easily tested and maintained. Similarly, a hexagonal architecture can use microservices architecture for deploying and scaling the system in the cloud infrastructure for example

# Dependency Injection

`Dependency injection (DI)` is a software design pattern that allows a program to remove hard-coded dependencies and make it more flexible, easier to maintain and test.

In object-oriented programming, dependencies often take the form of an object needing to use another object, and the way that these dependencies are typically handled is by creating them within the class that needs them. However, this tightly couples the class to its dependencies, making it more difficult to test and maintain.

Dependency injection allows a class to have its dependencies provided for it, rather than creating them itself. This is typically done by passing the dependencies in through the constructor or by using setter methods.

The pattern has different implementations for different languages and frameworks, like `inversion of control (IoC)` or `service locator patterns` are common patterns that are related and sometimes overlap with Dependency Injection.

Dependency injection frameworks are widely used to help implement DI in an application, many popular frameworks like Spring or Guice provide support for dependency injection. These frameworks often use reflection to automatically wire up the dependencies, so that developers don't need to manually create the instances of the dependencies and pass them in.

There are different ways to do dependency injection, like constructor injection, setter injection and interface injection.

* `Constructor injection`: the dependent object is passed to the constructor of the main object.
* `Setter injection`: the dependent object is passed to a setter method on the main object.
* `Interface injection`: the dependent object is passed to a non-constructor method, usually with an interface that represents the dependency.

In short, Dependency injection is a design pattern and practice to:

* avoid hardcoded dependencies.
* decouple the classes and make them more flexible
* make the code easier to test and maintain
* promote the use of a dependency injection framework.


# Inversion Of Controls 

`Inversion of Control (IoC)` is a software design principle that refers to a component that is being controlled by an external entity, rather than by itself. In other words, the flow of control of a system is inverted, so that instead of the component controlling the flow of the program, the program controls the flow of the component.

One common example of IoC is the use of a Dependency Injection (DI) container. A DI container is a component that manages the creation and lifecycle of objects, and is responsible for injecting their dependencies. When a class needs an instance of another class, it doesn't create it directly but instead, it asks the container to give it the instance. This inverts the control of the object creation and the control is transferred to the container.

IoC can also be achieved through other means such as the use of interfaces and callbacks. By defining an interface, you decouple the implementation from the usage and the implementation can be easily swapped out with another implementation that adheres to the same interface. Callbacks, also known as hooks, are methods that are defined by a component and are called by the system when certain events occur. This allows the component to participate in the flow of control, but the control itself is still inverted.

Inversion of Control can be seen as a more general principle and Dependency Injection a specific implementation of that principle. While Dependency Injection (DI) is a pattern that allows to implement IoC, other techniques like Service Locator, Event-Driven and template method pattern, allow to implement IoC too.

In summary, Inversion of Control (IoC) is a principle that:

* Inverts the flow of control by giving an external component control over the flow of a program
* Decouples the implementation from the usage
* Promotes flexibility and ease of maintenance by allowing different implementations to be swapped in and out.
* Can be achieved through different patterns or practices, like Dependency Injection or Service locator.

```typescript
interface Logger {
  log(message: string): void;
}

class ConsoleLogger implements Logger {
  log(message: string): void {
    console.log(message);
  }
}

class Application {
  private logger: Logger;

  constructor(logger: Logger) {
    this.logger = logger;
  }

  doSomething(): void {
    this.logger.log('doing something');
    // ...
  }
}

const logger = new ConsoleLogger();
const app = new Application(logger);
app.doSomething();
```

In this example, the `Application` class depends on a Logger interface. Instead of creating a new ConsoleLogger inside the Application class, it's created outside and passed to the constructor of the Application class. This way, we can easily swap the ConsoleLogger with a different implementation (e.g. a file logger) without changing the Application class.

Dependency injection helps to follow the SOLID principle of `Dependency inversion`, so that you can change how objects collaborate without changing the objects themselves.


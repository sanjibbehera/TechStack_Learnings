## Monoliths
A monolithic architecture is a traditional model for designing a software application where all the components are interconnected and interdependent. In this architecture, the application is built as a single, cohesive unit, and all functions run as a single process.  

**Features**:  
1. Single Codebase
2. Unified Deployment
3. Tightly Coupled
4. Shared Memory (Components share the same memory space, simplifies communication within the application)
5. Centralized Management

**Drawbacks**:  
1. Scalability Issues (Scaling parts of the application independently is difficult; the entire application must be scaled)
2. Maintenance Complexity (As the application grows, it becomes more complex and harder to understand and manage)
3. Deployment Bottlenecks (Small changes can require the entire application to be redeployed, increasing the risk of failure)
4. Limited Flexibility (Technology stack choices are limited since changing a technology affects the entire application)
5. Slow Development (Development can slow down as more teams work on the same codebase, leading to integration issues)
6. Fault Isolation (A bug in any module can potentially bring down the entire application)

## What Is a Modular Monolith?
A Modular Monolith is a software design approach in which a monolith is designed with an emphasis on interchangeable (and potentially reusable) modules.  
The problem with most monolith systems is that they become tightly coupled over time. Components are deeply intertwined. Making a change in one component impacts many others. Introducing new features is difficult and error-prone.

![Modular Monolith](Images/modular_monolith_diagram.png)

There are two widely used communication patterns.  
1. Synchronous Communication With Method Calls
   - Module A calls a method declared on the public API of Module B and waits until it receives a result.
2. Asynchronous Communication With Messaging
   - Module A sends a message to the message broker in a fire-and-forget fashion. Module B subscribes to relevant messages and handles them accordingly.
   - Modules don't need to know about each other, but they do need to know about the message contracts.



## Microservices
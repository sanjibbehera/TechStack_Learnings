## Monoliths


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
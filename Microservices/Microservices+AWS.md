# Microservices + AWS

## API gateway pattern
The API gateway pattern is recommended if you want to design and build complex or large microservices-based applications with multiple client applications.  
The pattern is similar to the facade pattern from object-oriented design, but it is part of a distributed system reverse proxy or gateway routing, and uses a synchronous communication model.  
An API gateway provides a single endpoint or URL for the client applications, and it internally maps the requests to internal microservices. A layer of abstraction is provided by hiding certain implementation details.

You should consider using the API gateway pattern if:
- The number of dependencies for a microservice is manageable and does not grow over time.
- The calling system requires a synchronous response from the microservice.
- You have low latency requirements.
- You need to expose one API to collect data from multiple microservices.

### Multiple API Gateways
![Multiple API Gateways](Images/Multiple_API_Gateway_solution.png?raw=true "Title")

### Single API Gateway
![Single API Gateways](Images/Single-api-gateway-solution.png?raw=true "Title")

## Decouple messaging pattern
This pattern provides asynchronous communication between microservices by using an asynchronous poll model.  
When the backend system receives a call, it immediately responds with a request identifier and then asynchronously processes the request.  
A loosely coupled architecture can be built, which avoids bottlenecks caused by synchronous communication, latency, and input/output operations (IO).

You should consider using the API gateway pattern if:
1. You want to create loosely coupled architecture.
2. All operations don’t need to be completed in a single transaction, and some operations can be asynchronous.
3. The downstream system cannot handle the incoming transactions per second (TPS) rate. The messages can be written to the queue and processed based on the availability of resources.

A disadvantage of this pattern is that business transaction actions are synchronous. Even though the calling system receives a response, some part of the transaction might still continue to be processed by downstream systems.

### Message decoupling with SQS
![Message decoupling with SQS](Images/message-decoupling-sqs.png?raw=true "Title")


## Pub/Sub pattern
The publish/subscribe (pub/sub) pattern provides asynchronous communication among multiple AWS services, such as Amazon SQS, Lambda or Amazon Simple Storage Service (Amazon S3), without creating interdependency.  
In this pattern, microservices publish events as messages in a channel that subscribers can listen to.

You should consider using the API gateway pattern if:
1. You have an event-driven architecture.
2. You can enable loosely coupled architecture.
3. You don't need to complete all operational parts of a transaction before the response back to the calling system (certain operations can be asynchronous).

There are several disadvantages to using this pattern.
1. The pub/sub pattern typically cannot guarantee delivery of messages to all subscriber types.
2. A publisher could assume that a subscriber is listening to a channel when, in fact, they are not.

### Pub/Sub Implementation with SNS
![Pub/Sub Implementation with SNS](Images/pub-sub-sns-impl.png?raw=true "Title")

### Pub/Sub Implementation with EventBridge
EventBridge filters events between multiple subscribers.  
The EventBridge implementation provides the following two options:
- Send events with different event types. The distant target picks them up based on the event rule.
- Send one message with three event rules listening to the same event type. Unnecessary data is filtered out before specific targets are invoked.

![Pub/Sub Implementation with EventBridge](Images/pub-sub-eventbridge-impl.png?raw=true "Title")


## Orchestration and state management
Microservices orchestration refers to a centralized approach, where a central component, known as the orchestrator, is responsible for managing and coordinating the interactions between microservices. Orchestrating workflows across multiple microservices can be challenging. Embedding orchestration code directly into services is discouraged, as it introduces tighter coupling and hinders replacing individual services.  
Step Functions provides a workflow engine to manage service orchestration complexities, such as error handling and serialization. This allows you to scale and change applications quickly without adding coordination code.

![Orchestration with Step Functions](Images/microservices-workflow-with-steps.png?raw=true "Title")

## Message bus pattern on AWS
![Message bus pattern on AWS](Images/message-bus-pattern.png?raw=true "Title")
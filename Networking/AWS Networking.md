# Networking

## Networking Fundamentals

### Different Layers of Computer Network

Physical Layer  
- This layer adds start and end delimiters to the message.
- Computers must agree on a contract to understand the encoded message.  

Routing Layer
- The process of sending message source to destination using intermediaries is known as routing.
- This layer is not strictly compulsory, because if some computer is listening on the physical layer, then they receive the message. However, it is useful when we know where to send the message because we don’t need to broadcast the message to all systems.
- When sending the message, the sender also includes the receiver’s address in the message. This message is then picked up by the router, it decodes the address and sends the message to the correct computer.
- To route the message to the correct computer and receive messages back we need
    - MAC Address This is like the identity of the computer system. It is permanent.
    - IP Address This is a virtual/logical/temporary address.
- Now, when sending a message, a sender can broadcast its IP Address. These routers then send the message forward until the correct computer receives it. Now if the receiver wants to send a message to the sender, they can do so easily.

Behavioral Layer
- This layer defines the conversation settings between two computers. This layer answers questions like
    - How frequently can one computer send messages to another?
    - Can the receiver after receiving a message, send a reply to the sender?
    - Can the receiver send a message without receiving any message?
- So we are defining the frequency, directions, and context of messages in this layer.

### Mapping these 3 layers to the OSI Model
![Mapping these 3 layers to the OSI Model](Images/Networking%20Models.webp?raw=true "Title")


### Connecting to the internet (So what happens when we enter a URL https://InterviewReady.com)
1. First, the computer sends this information to NIC (Network Interface Card). This hardware component allows the computer to connect to a network.
2. The NIC then allows the computer to connect to a router.
3. The Router does not know where https://InterviewReady.com is, so it asks a central authority. This central authority maps addresses to their IP Address. This central authority has a set of servers that help to find the IP Address (which is known as Internet Backbone). This is also known as Domain Name Server.
4. A Domain Name Server handles the mapping of a business domain name to an IP Address.
5. But how does this central authority know where https://InterviewReady.com is?
6. The configuration is done by InterviewReady on the servers.
7. After the router gets the IP Address, it connects to the InterviewReady Server through Network Protocol. To put it simply we go from router to router and every router. At every router, we get the address of the next router, which finally gets us to the InterviewReady Server.
8. Our router will also get a response similarly.

![Mapping these 3 layers to the OSI Model](Images/Connecting%20to%20Internet.webp?raw=true "Title")
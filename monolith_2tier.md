# Monolithic Architecture vs 2-Tier Architecture

## What is Monolithic Architecture

- It is a software architecture where the whole application is built as a single unit. All components of the application including the user interface, business logic and the data access layer are tightly integrated and deployed together. 
### Advantages
- Simple to develop and deploy
- Single codebases as it is all in application. 
### Disadvantages
- Scalability. It is challenging to scale horizontally as all components must be scaled together.
- Flexibility, making changes to the application can be complex as any modification to one part may require of the whole system.

## What is 2-Tier Architecture
- It is a software architecture pattern where the application is divided into two separate tiers or layers: the client tier and the server tier. Each tier has specific responsibilities and interacts with the other tier to accomplish tasks.

    Client Tier: This tier represents the user interface and application logic running on the client-side device.

    Server Tier: The server tier consists of the backend infrastructure responsible for processing requests from the client tier, executing business logic, and managing data




### Advantages
- Cost Effective. Lower developmental and maintenance costs.
- Performance. Reduces the amount of data transferred between the client and server. This leads to faster response times for user requests.
- Simplicity. Simple to design, maintain and implement. Only has two layers. 
- Scalability. Allows for both vertical and horizontal scalability.
### Disadvantages
- Single point of failure. If the server experiences downtime or malfuction, the entire system may be affected which can result in service distruptions.
- Security Concerns. Vulnerabilites in the server can potentially compromise the entire system. 







<div align="center" style="margin-top: 1em; margin-bottom: 3em;">

  <h1>INSIS Project</h1>
  <a><img alt="microservices" src=https://solace.com/wp-content/uploads/2020/05/microservices.png" alt="ethereum.org" width="125"></a>
  
  <!-- ALL-CONTRIBUTORS-BADGE:START - Do not remove or modify this section -->
[![All Contributors](https://img.shields.io/badge/all_contributors-3-darkgreen.svg?style=flate)](#contributors-url)
<!-- ALL-CONTRIBUTORS-BADGE:END -->
</div>

<!-- ABOUT THE PROJECT -->
The goal of this project is to reengineer the <a href="https://github.com/ana-rabelo/insis-monolithic-project" target="_blank">ACME application</a> by adopting a **decentralized/distributed** approach

- Two decentralization/distribution dimensions should be addressed:

    - <span style="color:#009639"><b>Business domain segregation</b></span>: the monolithic application must be segregated in three distinct but collaborating applications:
    
        (i) `Products`; 
        
        (ii) `Reviews`;
        
        (iii) `Votes`.

    - <b>Cloning</b>: Multiple instances of each of the previous application must be deployed in Virtual Machines or containers

<!-- REQUIREMENTS -->
### **Non-functional Requirements**
<hr />

- The following patterns must be adopted:

    - <b>`Strangler fig`</b>: incrementally migrate the monolithic system by gradually replacing specific pieces of functionality with new applications and services.
    - **`Command-Query Responsibility Segregation (CQRS)`**: separates read and update operations of each microservice for a data store 
    - **`Database-per-Service`**: keep each microservice’s persistent data private to that service and accessible only via its API. A service’s transactions only involve its database.
    - **`Polyglot persistence`**: involves using specialized database solutions when developing microservices, so each microservice can use a different type of database than the one used by another microservice.
    - **`Messaging`**: use asynchronous messaging for inter-service communication. Services communicating by exchanging messages over messaging channels.
    - **`The Domain Events`**: something that happened in the domain that you want other parts of the same domain (in-process) to be aware of. 
    - **`Event Sourcing`**: persists the state of a business entity such a Product or a Vote as a sequence of state-changing events. Whenever the state of a business entity changes, a new event is appended to the list of events. Since saving an event is a single operation, it is inherently atomic. The application reconstructs an entity’s current state by replaying the events.
    - **`Saga`**: a sequence of local transactions. Each local transaction updates the database and publishes a message or event to trigger the next local transaction in the saga. If a local transaction fails because it violates a business rule then the saga executes a series of compensating transactions that undo the changes that were made by the preceding local transactions.

 <p>


- AMQP Message Broker (e.g. RabbitMQ) must be adopted for communication between services. 
NB: External application endpoints should remain HTTP REST.

- Two or more frameworks/programming languages must be adopted in implementing the services.
- Deployment must be automated through CI/CD.
- Adoption of service component test pattern.
- Adoption of end-to-end test pattern. 
<p>

### **Functional Requirements**
<hr />

- Develop an endpoint in service Votes that allows <span style="color:#009639"><b>creating a vote for a non-existing review.</b></span> The review must be created for the specified product, and the vote is eventually associated with the review.

- Develop a <span style="color:#009639"><b>bootstrap process for the starting services.</b></span> I.e. at any time, a new service can start and its data must be bootstrapped.

<!-- BUILD -->
### **Built With**
<hr/>

- [![Docker][docker]][Docker-url]

- [![RabbitMQ][rabbitmq]][RabbitMQ-url]

- [![Spring][spring]][Spring-url]
    
- [![TypeScript][typescript]][typescript-url]

<!-- MARKDOWN LINKS & IMAGES -->
[docker]: https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white&style=flat
[Docker-url]: https://www.docker.com/
[RabbitMQ]: https://img.shields.io/badge/rabbitmq-%23FF6600.svg?&style=for-the-badge&logo=rabbitmq&logoColor=white&style=flat
[RabbitMQ-url]: https://www.rabbitmq.com/
[Spring]: https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white&style=flat
[Spring-url]: https://spring.io/
[Typescript]:https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white&style=flat
[typescript-url]:https://www.typescriptlang.org/

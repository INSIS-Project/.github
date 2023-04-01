<div align="center" style="margin-top: 1em; margin-bottom: 3em;">
  <a><img alt="microservices" src=https://i.imgur.com/BzkPOy8.png" alt="acme-project-header"></a>
</div>

<!-- ABOUT THE PROJECT -->
## About The Project

The goal of this project is to reengineer the <a href="https://github.com/ana-rabelo/insis-monolithic-project" target="_blank">ACME application</a> by adopting a **decentralized/distributed** approach.

- Two decentralization/distribution dimensions should be addressed:

    - <span style="color:#009639"><b>Business domain segregation</b></span>: the monolithic application must be segregated in three distinct but collaborating applications:
    
        (i) Products; 
        
        (ii) Reviews;
        
        (iii) Votes.

    - <span style="color:#009639"><b>Cloning</b></span>: Multiple instances of each of the previous application must be deployed in Virtual Machines or containers

### **Non-functional Requirements**
<hr />

- The following patterns must be adopted:

    - (Strangler fig)
    - Command-Query Responsibility Segregation (CQRS)
    - Database-per-Service
    - Polyglot persistence
    - Messaging
    - The Domain Events
    - Event Sourcing
    - Saga  <p>


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

### **Built With**
<hr/>

- [![Docker][docker]][Docker-url]

- [![RabbitMQ][rabbitmq]][RabbitMQ-url]

- [![Spring][spring]][Spring-url]
    
- [![TypeScript][typescript]][typescript-url]

<!-- MARKDOWN LINKS & IMAGES -->
[contributors]: https://img.shields.io/github/contributors/ana-rabelo/insis-project.svg?style=for-the-badge
[contributors-url]: https://github.com/ana-rabelo/insis-project/graphs/contributors
[docker]: https://img.shields.io/badge/Docker-2CA5E0?style=for-the-badge&logo=docker&logoColor=white
[Docker-url]: https://www.docker.com/
[RabbitMQ]: https://img.shields.io/badge/rabbitmq-%23FF6600.svg?&style=for-the-badge&logo=rabbitmq&logoColor=white
[RabbitMQ-url]: https://www.rabbitmq.com/
[Spring]: https://img.shields.io/badge/Spring-6DB33F?style=for-the-badge&logo=spring&logoColor=white
[Spring-url]: https://spring.io/
[Typescript]:https://img.shields.io/badge/TypeScript-007ACC?style=for-the-badge&logo=typescript&logoColor=white
[typescript-url]:https://www.typescriptlang.org/

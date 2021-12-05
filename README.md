# dotnet-microservices-training
Repository for my personal study of microservices architecture and implementation on .NET 5. Repository is based on the course https://www.udemy.com/course/microservices-architecture-and-implementation-on-dotnet

Shout out to **Mehmet Ozkaya** - *Initial work* -> [mehmetozkaya](https://github.com/mehmetozkaya)

## Overall chart of the architecture

![microservices](https://raw.githubusercontent.com/sebokoslav/dotnet-microservices-training/main/.github/assets/110304529-c5b70180-800c-11eb-832b-a2751b5bda76.png)

## Description of the microservices
Repository includes the following:

#### Catalog microservice which includes: 
* ASP.NET Core Web API application 
* REST API principles, CRUD operations
* **MongoDB database** connection and containerization
* Repository Pattern Implementation
* Swagger Open API implementation

#### Basket microservice which includes:
* ASP.NET Web API application
* REST API principles, CRUD operations
* **Redis database** connection and containerization
* Consuming Discount **Grpc Service** for inter-service sync communication to calculate product final price
* Publish BasketCheckout Queue with using **MassTransit and RabbitMQ**
  
#### Discount microservice which includes:
* ASP.NET **Grpc Server** application
* Highly Performant **inter-service gRPC Communication** with Basket Microservice
* Exposing Grpc Services with **Protobuf messages** creation
* Using **Dapper for micro-orm implementation** to simplify data access and ensure high performance
* **PostgreSQL database** connection and containerization

#### Microservices Communication
* Sync inter-service **gRPC Communication**
* Async Microservices Communication with **RabbitMQ Message-Broker Service**
* Using **RabbitMQ Publish/Subscribe Topic** Exchange Model
* Using **MassTransit** for abstraction over RabbitMQ Message-Broker system
* Publishing BasketCheckout event queue from Basket microservices and Subscribing this event from Ordering microservices	
* **RabbitMQ EventBus.Messages library** and add references to it in other microservices

#### Ordering Microservice
* Implementing **DDD, CQRS, and Clean Architecture** using Best Practices
* **CQRS with using MediatR, FluentValidation and AutoMapper packages**
* Consuming **RabbitMQ** BasketCheckout event queue using **MassTransit-RabbitMQ** Configuration
* **SqlServer database** connection and containerization
* **Entity Framework Core ORM** and SqlServer auto migration on application startup

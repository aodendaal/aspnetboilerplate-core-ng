[< Back to tutorial](README.md)

# Project Architecture

### Layers
* Presentation Layer - Interface for the user. Uses the Appplication Layer.
* Application Layer - Mediates between the Presentation and Domain Layers.
* Domain Layer - Contains the entities and business logic.
* Infrastructure Layer - Provides the specific implementation to connect to other services like the database as well as third-party libraries.

With regards to how the layers are implemented in our ASP\.NET Boilerplate template, the Presentation Layer is handled in the Angular project and the other layers in the ASP\.NET Core solution.

## Presentation Layer

## Application & Domain Layers

#### Module
An ASP\.NET Boilerplate application is composed of modules. A module registers services, providers and entities with the dependency injector. A module should be in its own assembly and each assembly in your solution should have a module.

So when you download a template, each project in the solution is a module and these have already been composed to create a basic application.

#### Application Service
Application services get and return Data Transfer Objects (DTOs)
An application service is used by the presentation layer to interact with the domain layer.

#### Domain Service
Domain Services get and return domain objects (entities or value types).
A domain service can be used by other domain services or by an application service but it cannot be used by the presentation layer.

## Infrastructure Layer

[< Back to tutorial](README.md)
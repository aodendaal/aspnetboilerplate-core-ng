# Project Architecture

## Layers
* __Presentation Layer__ - Interface for the user. Uses the Application Layer.
* __Application Layer__ - Mediates between the Presentation and Domain Layers.
* __Domain Layer__ - Contains the entities and business logic.
* __Infrastructure Layer__ - Provides the specific implementation to connect to other services like the database as well as third-party libraries.

With regards to how the layers are implemented in our ASP\.NET Boilerplate template, the Presentation Layer is handled in the Angular project and the other layers in the ASP\.NET Core solution.

## Presentation Layer
In our template this is handled entirely by Angular.

## Application & Domain Layers

### Module
An ASP\.NET Boilerplate application is composed of modules. A module registers services, providers and entities with the dependency injector. A module should be in its own assembly and each assembly in your solution should have a module.

So when you download a template, each project in the solution is a module and these have already been composed to create a basic application.

### Application & Domain Service
Application services get and return Data Transfer Objects (DTOs)
An application service is used by the presentation layer to interact with the domain layer.
In our template the application services and DTO classes are in the __.Application__ project

Domain Services get and return domain objects (entities or value types).
A domain service can be used by other domain services or by an application service but it cannot be used by the presentation layer.
In our template the domain services and entities are in the __.Core__ project

Both inherit from ```AbpServiceBase``` providing access to:
* SettingsManager
* UnitOfWorkManager
* LocalizationManager
* Logger
* ObjectMapper

## Security

See [User Manager, Roles & Permissions](usermanager.md) for more details.

## Infrastructure Layer
The __.EntityFrameworkCore__ and __.Web.Host__ projects represent the infrastructure layer.

## See Also
* [ASP\.NET Boilerplate Tutorials](readme.md)
* [How to Create an Domain Entity](entity.md)
* [How to Create an Application Service](applicationservice.md)

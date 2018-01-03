# Project Architecture

## Layers
* __Presentation Layer__ - Interface for the user. Uses the Application Layer.
* __Application Layer__ - Mediates between the Presentation and Domain Layers.
* __Domain Layer__ - Contains the entities and business logic.
* __Infrastructure Layer__ - Provides the specific implementation to connect to other services like the database as well as third-party libraries.

With regards to how the layers are implemented in our ASP\.NET Boilerplate template, the Presentation Layer is handled in the Angular project and the other layers in the ASP\.NET Core solution.

## Presentation Layer
In the ABP template this is handled entirely by Angular.

## Application & Domain Layers

### Module
An ASP\.NET Boilerplate application is composed of modules. A module registers services, providers and entities with the dependency injector. A module should be in its own assembly and each assembly in your solution should have a module.

So when you download a template, each project in the solution is a module and these have already been composed to create a basic application.

### Application Layer
The application layer is the interface between the presentation layer, any third-party applications and the business rules in the domain layer.

It is responsible for authorization, data validation and converting the business objects into data transfer objects (DTOs) and vice versa.

The layer is made up of one or more __Application Services__ and __Data Transfer Objects__.

In the ABP template the application services and DTO classes are in the __.Application__ project.

### Domain Layer
The domain layer contains the domain entities and business rules of the applacation as well as any definitions. It is the heart of the application.

The domain layer is made up of one or more __Domain Services__, conventionally called _Domain Managers_ to avoid confusion with application services.

Domain Services get and return domain objects (entities or value types).

A domain service can be used by other domain services or by an application service but it cannot be used by the presentation layer.

In the ABP template the domain services and entities are in the __.Core__ project

### AppServiceBase
Application Services and Domain Services both inherit from ```AbpServiceBase``` providing access to:
* SettingsManager
* UnitOfWorkManager
* LocalizationManager
* Logger
* ObjectMapper

### Security

See [User Manager, Roles & Permissions](usermanager.md) for more details.

## Infrastructure Layer
The __.EntityFrameworkCore__ and __.Web.Host__ projects represent the infrastructure layer.

## See Also
* [ASP\.NET Boilerplate Tutorials](readme.md)
* [How to Create an Domain Entity](entity.md)
* [How to Create an Application Service](applicationservice.md)

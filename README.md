# ASP\.NET Boilerplate Tutorials
This is a set of tutorials I've created for my junior team using ASP\.NET Boilerplate. Specifically ASP\.NET Boilerplate using ASP\.NET Core running on \.NET Core with the Angular 2 SPA.

## Prerequisites Tools
* Visual Studio 2017
* VSCode
* NodeJS

## Prerequisite Understanding
### \.NET Core
\.NET Core can be thought of as a cross-platform version of the \.NET Framework supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios. It implements the \.NET Standard Library specification.

### ASP\.NET Core
ASP\.NET Core is no longer based on __System.Web.dll__
ASP\.NET Core apps can run on \.NET Core or on the full \.NET Framework

### Entity Framework Core
The technology formerly known as Entity Framework 7 (EF7) was renamed to Entity Framework Core (EF Core) in early 2016 but that doesn't mean it only runs on \.NET Core. EF Core can run on the full \.NET Framework or on \.NET Core.

### Angular
Angular is an open-source frontend web application platform

# Tutorials
* [How to Initialize and Run a Clean Template](cleantemplate.md)
* [How to Create an Entity](#how-to-create-an-entity)
* [How to Update the Database](#how-to-update-the-database)
* [How to Create an Application Service](#how-create-an-application-service)

# Other Articles
* [Localization](localization.md)

# How to Create an Entity
TODO
# How to Update the Database
TODO
# How to Create an Application Service
* [Unit of Work](#unit-of-work)
* [Hide from Controller](#hide-from-controller)

### Unit of Work
By default functions in an application service are transactional, meaning if there's an exception in the function then all repository functions are rolled back. It can be turned off by adding the ```UnitOfWork``` attribute to your function and setting ```IsDisabled``` to ```true```.
```csharp
[UnitOfWork(IsDisabled: true)]
```
### Hide from Controller
The __.Web.Core__ module is configured to generate WebAPI controllers for any application services found in __.Application__. To prevent a specific application service or function in a service from being generated, add the ```RemoteService``` attibute and set ```isEnabled``` to ```false```.
```csharp
[RemoteService(isEnabled: false)]
```

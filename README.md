# ASP\.NET Boilerplate Tutorials
This is a set of tutorials I've created for my junior team using [ASP\.NET Boilerplate](https://www.aspnetboilerplate.com).

These tutorials are also mostly applicable to ABP 3.4.

## Prerequisites Tools
* Visual Studio 2017
* VSCode
* NodeJS
* [Yarn](https://yarnpkg.com)

## Prerequisite Understanding
### \.NET Core
\.NET Core can be thought of as a cross-platform version of the \.NET Framework supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios. It implements the \.NET Standard Library specification.

### ASP\.NET Core
ASP\.NET Core is no longer based on __System.Web.dll__
ASP\.NET Core apps can run on \.NET Core or on the full \.NET Framework

Make sure to install .NET Core 2.0 SDK

### Entity Framework Core
The technology formerly known as Entity Framework 7 (EF7) was renamed to Entity Framework Core (EF Core) in early 2016 but can run on the full \.NET Framework or on \.NET Core.

### Angular
[Angular](http://angular.io) is an open-source frontend web application platform

### RxJS
[RxJS](http://reactivex.io/rxjs/) is a library for composing asynchronous and event-based programs by using observable sequences. [This article](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754) is a very good introduction to reactive programming.

### AdminBSB
ABP uses [AdminBSB](https://github.com/gurayyarar/AdminBSBMaterialDesign), a free admin panel that is based on Bootstrap 3.x with Material Design. You can find working examples of all the input and components [here](https://gurayyarar.github.io/AdminBSBMaterialDesign/index.html).

The old template (version 2.0.2)  uses [ngx-bootstrap](http://valor-software.com/ngx-bootstrap/#/) which contains all core (but not only) Bootstrap components powered by Angular. This also includes [moment.js](http://momentjs.com/) for parsing and manipulating dates.

### ABP API
While not a requisite (since we're coving most of it in depth in this tutorial) the API specification is also available [online](https://aspnetboilerplate.com/api-docs/html/R_Project_Documentation.htm)

## Starting Articles
* [How to Initialize and Run a Clean Template](docs/cleantemplate.md)
* [Project Architecture](docs/projectarchitecture.md)

## Deployment
* [Deploying to Azure](docs/deployment.md)
* [Determining Current Tenant](https://aspnetboilerplate.com/Pages/Documents/Multi-Tenancy#determining-current-tenant) - Link to ASP.NET Boilerplate documentation
* [Accessing the server log from Azure](docs/serverlog.md)

## Infrastructure Layer
* [Creating a Custom Repository](docs/customrepos.md)
* [Writing to the server log file](docs/serverlog.md)
* [Enabling Social Login](docs/sociallogin.md)

## Domain Layer
* [How to create an entity](docs/entity.md)
* [User Manager, Roles & Permissions](docs/usermanager.md)
* [Localization](docs/localization.md)
* [Background Jobs](docs/backgroundjobs.md)

## Application Layer
* [How to Create an Application Service](docs/applicationservice.md)
* [Overriding the CRUD Application Service](docs/crudappservice.md)
* [Communicating with the Application Layer](docs/restapi.md)
* [Using Predefined Permissions](docs/permissions.md)
* [Integrate ASPNET Core SignalR](docs/coresignalerintegration.md)
* [Throwing HTTP Error Codes](docs/exceptions.md)

## Presentation Layer
* [Built-in Functions](docs/angularbuiltin.md)
* [Creating modal dialogs](docs/modals.md)
* [Updating the Menu](docs/menu212.md) (version 2.1.2 only)
* [Read URL query parameters](docs/routing.md)
* [Including JavaScript libraries](docs/libraries.md)
* [Using SignalR](docs/signalr.md)
* [What is the 'clearfix' class for?](docs/clearfix.md)
* [ExpressionChangedAfterItHasBeenCheckedError](https://blog.angular-university.io/angular-debugging/)

## AppFactory Customizations
* [Entity Not Found Exception](https://gist.github.com/aodendaal/86fedc36b3593a4adbd4e35ef0327702)
* [Angular 2 User Profile Self-Help Editor](https://github.com/aodendaal/abp-ng2-profile-editor)
* [Azure Blob Storage Module](https://github.com/aodendaal/abp-appfactory-blobprovider)
* [Migration Automation for Continuous Deployment](docs/automigrations.md)

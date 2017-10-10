# ASP\.NET Boilerplate Tutorials
This is a set of tutorials I've created for my junior team using [ASP\.NET Boilerplate](https://www.aspnetboilerplate.com). Specifically ASP\.NET Boilerplate __2.0.2__ using ASP\.NET Core running on \.NET Core with the Angular 2 SPA (also known as ASP\.NET Boilerplate Core & Angular).

These tutorials are also mostly applicable to ABP 2.1.2.

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
The technology formerly known as Entity Framework 7 (EF7) was renamed to Entity Framework Core (EF Core) in early 2016 but can run on the full \.NET Framework or on \.NET Core.

### Angular
[Angular](http://angular.io) is an open-source frontend web application platform

### RxJS
[RxJS](http://reactivex.io/rxjs/) is a library for composing asynchronous and event-based programs by using observable sequences. [This article](https://gist.github.com/staltz/868e7e9bc2a7b8c1f754) is a very good introduction to reactive programming.

### ngx-bootstrap
The 2.0.2 template uses [ngx-bootstrap](http://valor-software.com/ngx-bootstrap/#/) which contains all core (but not only) Bootstrap components powered by Angular. This also includes [moment.js](http://momentjs.com/) for parsing and manipulating dates.

### __2.1.2__ AdminBSB
Later versions of ABP use [AdminBSB](https://github.com/gurayyarar/AdminBSBMaterialDesign), a free admin panel that is based on Bootstrap 3.x with Material Design. You can find working examples of all the input and components [here](https://gurayyarar.github.io/AdminBSBMaterialDesign/index.html).

## Main Articles
* [How to Initialize and Run a Clean Template](cleantemplate.md)
* [Project Architecture](projectarchitecture.md)
* [Reading Module Configuration From AppSettings](moduleconfig.md)

## Deployment
* [Deploying to Azure](deployment.md)
* __2.1.2__ Using Docker to deploy to Azure
* [Determining Current Tenant](https://aspnetboilerplate.com/Pages/Documents/Multi-Tenancy#determining-current-tenant) - Link to ASP.NET Boilerplate documentation

## Infrastructure Layer
* How to Update the Database
* [Adding Email Verification using SendGrid](emailverification.md) - A practical exercise extending ASP\.NET Boilerplate
* [Create a Custom Repository](customrepos.md)

## Domain Layer
* [How to Create an Entity](entity.md)
* [User Manager, Roles & Permissions](usermanager.md)
* [Localization](localization.md)

## Application Layer
* [How to Create an Application Service](applicationservice.md)

## Presentation Layer
* How to Create a Component
* [Built-in Functions](angularbuiltin.md)
* [Creating modal dialogs](modals.md)
* Adding a datepicker
* Adding a searchable/type-ahead drop-down list
* __2.1.2__ [Updating the Menu](menu212.md)
* [Read URL query parameters](routing.md)
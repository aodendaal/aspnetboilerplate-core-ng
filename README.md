# ASP\.NET Boilerplate Tutorials
* [How to Initialize and Run a Clean Template](#how-to-initialize-and-run-a-clean-template)
* [How to Create an Entity](#how-to-create-an-entity)
* [How to Update the Database](#how-to-update-the-database)
* [How to Create an Application Service](#how-create-an-application-service)

# How to Initialize and Run a Clean Template
1. [Download ASP\.NET Boilerplate template](#1-download-template)
2. [Fix EFCore Versions & Add DotNet Tooling](#2-fix-efcore-versions--add-dotnet-tooling)
3. [Change Database Connection String](#3-change-database-connection-string)
4. [Restore NuGet Packages](#4-restore-nuget-packages)
5. [Create Database](#5-create-database)
6. [Run Backend](#6-run-backend)
7. [Install NPM Dependencies](#7-install-npm-dependencies)
8. [Refresh Swagger Proxies](#8-refresh-swagger-proxies)
9. [Run Frontend](#9-run-frontend)

### Prerequisites Tools
* Visual Studio 2017
* VSCode
* NodeJS

### Prerequisite Understanding
#### \.NET Core
\.NET Core can be thought of as a cross-platform version of the \.NET Framework supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios. It implements the \.NET Standard Library specification.

#### ASP\.NET Core
ASP\.NET Core is no longer based on __System.Web.dll__
ASP\.NET Core apps can run on \.NET Core or on the full \.NET Framework

#### Entity Framework Core
The technology formerly known as Entity Framework 7 (EF7) was renamed to Entity Framework Core (EF Core) in early 2016 but that doesn't mean it only runs on \.NET Core. EF Core can run on the full \.NET Framework or on \.NET Core.

#### Angular
Angular is an open-source frontend web application platform

## 1. Download template
Goto the [ASP.NET Boilerplate](https://www.aspnetboilerplate.com) website and download the ASP\.NET Core 1.x template using the .NET Core 1.1 framework, select Single Page Web Application using Angular 2 and make sure Include module-zero is checked.

## 2. Fix EFCore Versions & Add DotNet Tooling
Edit _project.EntityFrameworkCore.csproj_ found in the __/aspnet-core/src/project.EntityFrameworkCore__ directory and update the references to the ones below:
```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="1.1.1" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.1" />
  </ItemGroup>
```
Note there is an extra reference added to enable using the Entity Framework Core CLI. Now add the CLI tool reference:
```xml
  <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.1" />
  </ItemGroup>
```

## 3. Change Database Connection String
Edit _appsettings.json_ in __.Web.Host__ to change the connection string to use __localdb__.
```javascript
  "ConnectionStrings": {
    "Default": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=PeopleProject;"
  }
```

## 4. Restore NuGet Packages
We will use the .NET Core Shared Framework Host to restore the projects' NuGet packages and run our Entity Framework Core commands.

Open PowerShell, navigate to the __/aspnet-core__ directory and run
```powershell
dotnet restore
```

## 5. Create Database
Still in PowerShell go to the __.EntityFrameworkCore__ directory and run
```powershell
dotnet ef database update
```

## 6. Run Backend
Start Visual Studio 2017 and open the solution. Set the __.Web.Host__ project as the Startup Project and debug the solution.

## 7. Install NPM Dependencies
In the __/angular__ directory run:
```powershell
npm install
```
This will take some time while it downloads all the dependencies.

## 8. Refresh Swagger Proxies
While not technically necessary now navigate to the __/angular/nswag__ directory and run:
```powershell
refresh.bat
```

## 9. Run Frontend
Return to the __/angular__ directory and run:
```powershell
npm start
```
This will start the frontend as well as the continuous transpiling so that as you edit the typescript and HTML files and save the code is immediately compiled and the application refreshed.

Open a web browser and navigate to the client site:
```
http://localhost:4200
```
# Congratulations! We're halfway there!
> At this point we've downloaded, initialized and run the bare template. Well done on making it this far.
> Now we can start to create our own customizations on top of the ASP\.NET Boilerplate platform.

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

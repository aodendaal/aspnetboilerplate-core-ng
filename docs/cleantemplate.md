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

## 1. Download template
Goto the [ASP.NET Boilerplate](https://www.aspnetboilerplate.com) website and download the ASP\.NET Core 1.x template using the .NET Core 1.1 framework, select Single Page Web Application using Angular 2 and make sure Include module-zero is checked.

## 2. Fix EFCore Versions & Add DotNet Tooling
_This step is specific to ABP 2.0.2 and can be ignored for later versions._

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
Edit the _appsettings.json_ file in the __.Web.Host__ folder, and update the connection string to change the *Data Source* to use __localdb__.
```javascript
  "ConnectionStrings": {
    "Default": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=PeopleProject;"
  }
```
*Initial Catalog* is the name you want to use for the database.

## 4. Restore NuGet Packages
We will use the .NET Core Shared Framework Host (`dotnet`) to restore the projects' NuGet packages and run our Entity Framework Core commands.

Open PowerShell, navigate to the __/aspnet-core__ directory and run
```powershell
dotnet restore
```

## 5. Create Database
Still in PowerShell go to the __.EntityFrameworkCore__ directory and run

```powershell
dotnet ef
```

If you don't see the unicorn, something has gone wrong. Otherwise run

```powershell
dotnet ef database update
```

## 6. Run Backend
Start Visual Studio 2017 and open the solution. Set the __.Web.Host__ project as the Startup Project and debug the solution.

## 7. Install NPM Dependencies
In the __/angular__ directory run:
```powershell
yarn install
```

_Versions before 2.3.0 use NPM instead of Yarn._
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
yarn start
```

_Versions before 2.3.0 use NPM instead of Yarn._
```powershell
npm start
```

This will start the frontend as well as the continuous transpiling so that as you edit the typescript and HTML files and save the code is immediately compiled and the application refreshed.

Open a web browser and navigate to the client site:
```
http://localhost:4200
```
# Congratulations! We're done!
> At this point we've downloaded, initialized and run the bare template. Well done on making it this far.
> Now we can start to create our own customizations on top of the ASP\.NET Boilerplate platform.

## See Also
* [ASP\.NET Boilerplate Tutorials](../README.md)
* [Project Architecture](projectarchitecture.md)
* [Reading Module Configuration From AppSettings](moduleconfig.md)
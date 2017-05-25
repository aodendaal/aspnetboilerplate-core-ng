# Tutorial Steps
1. [Download ASP\.NET Boilerplate template](#download-template)
2. Fix EFCore Versions & Add DotNet Tooling
3. Change Database Connection String
4. Restore NuGet Packages
5. Create Database
6. Run Backend
7. Install NPM Dependencies
8. Refresh Swagger Proxies
9. [Run Frontend](#9.-run-frontend)

### Prerequisites Tools
* Visual Studio 2017
* VSCode
* NodeJS

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
Edit _appsettings.json_ in __/aspnet-core/src/project.Web.Host__ to change the connection string to use __localdb__.
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

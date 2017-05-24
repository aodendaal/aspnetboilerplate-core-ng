# Tutorial Steps
1. Download ASP\.NET Boilerplate template
2. Fix EFCore Versions & Add DotNet tooling
3. Change database connection string
4. Restore NuGet packages
5. Create database
6. 

### Prerequisites
* Visual Studio 2017

### Prerequisite Understanding
* .NET Core
* ASP\.NET Core

## 1. Download template
Goto the [ASP.NET Boilerplate](https://www.aspnetboilerplate.com) website and download the ASP\.NET Core 1.x template using the .NET Core 1.1 framework, select Single Page Web Application using Angular 2 and make sure Include module-zero is checked.

## 2. Fix EFCore Versions & Add DotNet tooling
Edit __.EntityFrameworkCore__ project file references
```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="1.1.1" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.1" />
  </ItemGroup>
```
And add the CLI reference
```xml
  <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.1" />
  </ItemGroup>
```

## 3. Change database connection String
Edit _appsettings.json_ in __.Web.Host__ to change connection string to __localdb__.
```javascript
  "ConnectionStrings": {
    "Default": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=PeopleProject;"
  }
```

## 4. Restore NuGet packages
Open Powershell, navigate to the __.sln__ directory and run
```powershell
dotnet restore
```

## 5. Create database
Still in PowerShell go to the __.EntityFrameworkCore__ directory and run
```powershell
dotnet ef database update
```

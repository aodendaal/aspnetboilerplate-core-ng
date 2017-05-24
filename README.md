## Important config settings

__.Web.Host__ appsettings.json connection string for __localdb__.
```javascript
  "ConnectionStrings": {
    "Default": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=PeopleProject;"
  }
```
__.EntityFrameworkCore__ project references
```xml
  <ItemGroup>
    <PackageReference Include="Microsoft.EntityFrameworkCore" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.SqlServer" Version="1.1.2" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Tools" Version="1.1.1" />
    <PackageReference Include="Microsoft.EntityFrameworkCore.Design" Version="1.1.2" />
	<PackageReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.1" />
  </ItemGroup>
```
__.EntityFrameworkCore__  CLI reference
```xml
  <ItemGroup>
    <DotNetCliToolReference Include="Microsoft.EntityFrameworkCore.Tools.DotNet" Version="1.0.1" />
  </ItemGroup>
```

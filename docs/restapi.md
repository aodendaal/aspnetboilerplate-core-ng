# REST API
The application layer is exposed as a REST service hosted on ASP.NET Core.

ABP uses [Swagger.io](https://swagger.io) to document the end points as well as provide a handy user interface to directly interact with the backend.

## Authentication and passing the Tenant Id

The tenant id is determined in the following order:
1. Via the URL
2. Via the **Abp.TenantId** key-value pair in the header
3. Via a cookie

## Using strings for enumerations
Open **Startup.cs** in .Web.Host/Startup and in the ```services.AddSwaggerGen``` scope add the following line:

```cs
services.AddSwaggerGen(options =>
{
    ...
    options.DescribeAllEnumsAsStrings();
}
```

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [How to Create an Application Service](applicationservice.md)
* [Overriding the CRUD Application Service](crudappservice.md)
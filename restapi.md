# REST API
The application layer is exposed as a REST service hosted on ASP.NET Core.

## Authentication and passing the Tenant Id

The tenant id is determined in the following order:
1. Via the URL
2. Via the **Abp.TenantId** key-value pair in the header
3. Via a cookie

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [How to Create an Application Service](applicationservice.md)
* [User Manager, Roles & Permissions](usermanager.md)
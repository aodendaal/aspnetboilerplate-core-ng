# User Manager, Roles & Permissions

## UserManager

* SetRoles
* RemoveFromRoleAsync
* RemoveFromRolesAsync

## Lock outs
By default, ABP locks a user's login for 5 minutes if they incorrectly enter their password 5 times. The count resets when the login is locked or when the user enters the correct password.

![lockout message](/img/lockout.png "lockout message")

When a new user is created `IsLockoutEnabled` is `True` by default. `AccessFailedCount` stores the number of failed attempts to login. `LockoutEndDateUtc` stores when the account will be available again.

## Roles & Permissions

### Permissions

A **permission** should encapsulate a single feature in your application such as: displaying a menu, viewing a page, enabling a button on a form, or editing an entity.

While a permission name can take any form, my recommendation is to use a *Verb Noun*, denoting the action permitted such as ```ViewHomepage```, ```ManageUsers```, or ```DeleteTenant```. Do not mention a role in a permission name because multiple roles can inherit a permission.

Permission names are defined as static fields in **.Core/Authorization/PermissionNames.cs**. The permissions themselves are defined in **.Core/Authorization/ProjectNameAuthorizationProvider.cs**.

### Roles

A **role** can have zero to many permissions. A role can be set as default which will then be assigned to newly registered users in a clean ABP template.

A user can have zero to many roles.

Role names are defined as static fields in **.Core/Authorization/Roles/StaticRoleNames.cs**. 

The role is created and linked to permissions in **.EntityFrameworkCore/EntityFrameworkCore/Seed/Host/HostRoleAndUserCreator.cs** or **.EntityFrameworkCore/EntityFrameworkCore/Seed/Tenants/TenantRoleAndUserBuilder.cs** depending if it is a host or tenant role.

For creating new tenants, static roles must be defined in **.Core/Authorization/Roles/AppRoleConfig.cs**

```cs
roleManagementConfig.StaticRoles.Add(
    new StaticRoleDefinition(
        StaticRoleNames.Tenants.Admin,
        MultiTenancySides.Tenant)
    
roleManagementConfig.StaticRoles.Add(
    new StaticRoleDefinition(
        StaticRoleNames.Tenants.EndUser,
        MultiTenancySides.Tenant)
    );
```

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Project Architecture](projectarchitecture.md)
* [How to Create an Application Service](applicationservice.md)
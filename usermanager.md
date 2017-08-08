# User Manager, Roles & Permissions

## UserManager

* SetRoles
* RemoveFromRoleAsync
* RemoveFromRolesAsync

## Roles & Permissions

A **permission** should encapsulate a single feature in your application such as: showing a menu option, viewing a page, enabling buttons on form, or editing an entity. A permission can also be a collection of permissions e.g. a full entity permission which contains the: create, update, retrieve & delete permissions.

A **role** can have zero to many permissions. A role can be set as default which will then be assigned to newly registered users in a clean ABP template.

A user must have one to many roles.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Project Architecture](projectarchitecture.md)
* [How to Create an Application Service](applicationservice.md)
# User Manager, Roles & Permissions

## UserManager

* SetRoles
* RemoveFromRoleAsync
* RemoveFromRolesAsync

## Roles & Permissions

A **permission** should encapsulate a single feature in your application such as: displaying a menu, viewing a page, enabling a button on a form, or editing an entity. A permission can also be a collection of permissions e.g. a full entity permission which contains the: create, update, retrieve & delete permissions for that entity.

While a permission name can take any form, my recommendation is to use a *Verb Noun* denoting the action permitted such as ```ViewHomepage```, ```ManageUsers```, or ```DeleteTenant```. Do not mention a role in a permission name because multiple roles can inherit a permission.

A **role** can have zero to many permissions. A role can be set as default which will then be assigned to newly registered users in a clean ABP template.

A user must have one to many roles.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Project Architecture](projectarchitecture.md)
* [How to Create an Application Service](applicationservice.md)
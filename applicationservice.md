# Creating an Application Service

## Using built-in CRUD application Service

```csharp
public class EntityAppService : CrudAppService<Entity, EntityDto>
{
    public EntityAppService(IRepository<Entity> repository): base(repository)
}
```

Or as asynchronous

```csharp
public class EntityAppService : AsyncCrudAppService<Entity, EntityDto>
{
    public EntityAppService(IRepository<Entity> repository): base(repository)
}
```

When overriding or extending the application service use the base repository ```Repository```.

## Injecting Domain Services
There are a couple of ways of injecting domain services (or even other application services, but this is not recommended). The dependency injector looks at the datatype passed (the interface or class name) to determine what to inject so the variable name can be anything you want.

**Example: Injection via the Constructor**

```csharp
public class EntityAppService: projectAppServiceBase
{
    private readonly IEntityDomainService entityManager;

    public EntityAppService(
        IEntityDomainService entityManager
    )
    {
        this.entityManager = entityManager;
    }
    
    ...
}
```

**Example: Injection via a Public Property**

```csharp
public class EntityAppService: projectAppServiceBase
{
    public IEntityDomainService EntityManager { get; set; }

    public EntityAppService()
    {
    }
    
    ...
}
```

## Security

```csharp
[AbpAuthorize(params string[] permissions)]
```

See [User Manager, Roles & Permissions](usermanager.md) for more details.

## Unit of Work
The UnitOfWorkManager is injected by default into MVC Controllers, application services & domain services. This means functions in an application service are transactional, i.e. if there's an exception in the function then all repository functions are rolled back.

It can be turned off by adding the ```UnitOfWork``` attribute to your function and setting ```IsDisabled``` to ```true```. However, **if a unit of work function calls a function where the unit of work is disabled, the disable is ignored and it will use the same connection & transaction**.
```csharp
[UnitOfWork(IsDisabled: true)]
```

You can also use Unit of Work to impersonate another tenant

```csharp
using (_unitOfWorkManager.Current.SetTenantId(input.TentantId))
{
} 
```

## Hide from Controller
The __.Web.Core__ module is configured to generate WebAPI controllers for any application services found in __.Application__. To prevent a specific application service or function in a service from being generated, add the ```RemoteService``` attibute and set ```isEnabled``` to ```false```.
```csharp
[RemoteService(isEnabled: false)]
```

## Function Names
HTTP verbs are determined by method name prefixes, otherwise __Post__ is used as default HTTP verb. You can also override or specify a preferred method using the the HTTP-verb attributes found in Microsoft.AspNet.WebApi.Core.

* __Get:__ Used if method name starts with 'Get'.
* __Put:__ Used if method name starts with 'Put' or 'Update'.
* __Delete:__ Used if method name starts with 'Delete' or 'Remove'.
* __Post:__ Used if method name starts with 'Post', 'Create' or 'Insert'.
* __Patch:__ Used if method name starts with 'Patch'.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Project Architecture](projectarchitecture.md)
* [Frontend Built-in Functions](angularbuiltin.md)

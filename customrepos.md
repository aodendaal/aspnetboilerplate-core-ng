# Creating a Custom Repository

You should always strive to maintain the _Domain-Driven Design (DDD)_ and _Separation of Concerns_ by creating a custom repository in the **.EntityFrameworkCore** which you can then inject into the application or domain layers.

1. Create a repository interface in **.Core**
2. Create the repository implementation in **.EntityFrameworkCore** in Repositories
    1. Inherit from ```EfCoreRepositoryBase``` and your interface
    2. Inject ```IDbContextProvider``` and ```IActiveTransactionProvider``` into the constructor
    3. Create private fields to reference the injected objects
3. Add the custom functions for your repository
4. Use the custom repository in your domain service

Each step is explained in more detail below.

## Creating a Repository Interface

Create an interface in the **.Core** project which inherits from `IRepository`. The reason this is created in the **.Core** project is so it can accessed by the rest of the solution
```csharp
using Abp.Domain.Repositories;

namespace ExampleProject
{
  public interface IEntityRepository : IRepository<Entity>
  {
    Entity DoSomething();
  }
}
```

## Creating the Repository Implementation
In your **.EntityFrameworkCore** project create a public class that implements your new repository interface.

```csharp
public class EntityRepository
{

}
```

Inherit from `EfCoreRepositoryBase`

Below is the full listing:

```csharp
using System.Data.Common;
using Abp.Data;
using Abp.EntityFrameworkCore;
using Abp.EntityFrameworkCore.Repositories;
using Microsoft.EntityFrameworkCore;
using SeeSayDo.Content;

namespace ExampleProject.EntityFrameworkCore.Repositories
{
    public class EntityRepository : EfCoreRepositoryBase<ExampleProjectDbContext, Entity>, IEntityRepository
    {
        private readonly IDbContextProvider<ExampleProjectDbContext> contextProvider;
        private readonly IActiveTransactionProvider transactionProvider;

        public ContentPieceRepository(
            IDbContextProvider<SeeSayDoDbContext> dbContextProvider,
            IActiveTransactionProvider transactionProvider
            ) : base(dbContextProvider)
        {
            this.contextProvider = dbContextProvider;
            this.transactionProvider = transactionProvider;
        }
    }
}
```

## Adding functions to the custom repository

We still need to implement the function we defined in our interface that will call the stored procedure.

```csharp
public Entity DoSomething()
{
    var entity = new Entity();

    using (var context = contextProvider.GetDbContext())
    {
        var connection = context.Database.GetDbConnection();

        var command = connection.CreateCommand();
        command.CommandText = "sp_DoSomething";
        command.CommandType = System.Data.CommandType.StoredProcedure;
        command.Transaction = (DbTransaction)transactionProvider.GetActiveTransaction(new ActiveTransactionProviderArgs
            {
                {"ContextType", typeof(ExampleProjectDbContext) },
                {"MultiTenancySide", MultiTenancySide }
            });

        context.Database.OpenConnection();

        using (var reader = command.ExecuteReader())
        {
            entity.Id = (int)reader["Id"];
            ...
        }
    }

    return entity;
}
```

## Using the Custom Repository

To use your custom repository, inject the interface into your application or domain service via the constructor and call your custom function. Because you inherited IRepository, all the other repository features are also available so you don't need to inject a generic repository as well as your custom one.

```csharp
using System;
using Abp.Domain.Repositories;
using Abp.Domain.Services;

namespace ExampleProject.Entities
{
    public class EntityManager : DomainService
    {
        private readonly IEntityRepository customRepository;

        public EntityManager(
            IContentPieceRepository customRepository
            )
        {
            this.customRepository = customRepository;
        }

        public Entity DoSomething()
        {
            return contentRepository.DoSomething();
        }
    }
}
```

## Adding the Stored Procedure During Seeding
In the migration you can use `SQL()` to add a script.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Adding Email Verification using SendGrid](emailverification.md)
* How to Update the Database
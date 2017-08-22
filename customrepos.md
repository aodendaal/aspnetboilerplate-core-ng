# Create a Custom Repository

1. Create a repository interface in **.Core**
2. Create a new class in **.EntityFrameworkCore** in Repositories
3. Inherit from ```EfCoreRepositoryBase``` and your interface
4. Inject ```IDbContextProvider``` and ```IActiveTransactionProvider``` into the constructor
5. Create private fields to reference the injected objects

## Using Transactions

**Example:**
```csharp
public Entity Get()
{
    var entity = new ContentPiece();

    using (var context = contextProvider.GetDbContext())
    {
        var connection = context.Database.GetDbConnection();
        
        DbCommand command = connection.CreateCommand();
        command.CommandText = "GetNext";
        command.CommandType = System.Data.CommandType.StoredProcedure;
        command.Transaction = (DbTransaction)transactionProvider.GetActiveTransaction(new ActiveTransactionProviderArgs
            {
                {"ContextType", typeof(SeeSayDoDbContext) },
                {"MultiTenancySide", MultiTenancySide }
            });

        context.Database.OpenConnection();

        using (var reader = command.ExecuteReader())
        {
            entity.Id = reader.GetInt32(0);
        }
    }

    return entity;
}
```

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Adding Email Verification using SendGrid](emailverification.md)
* How to Update the Database
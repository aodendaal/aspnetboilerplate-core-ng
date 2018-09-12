# Auto Migrations
 
 Allow ABP to migrate itself on startup
 
## Add Migration Helper

add the following class to EF Seed folder:

```cs
using Abp.Dependency;
using Abp.Domain.Uow;
using Abp.EntityFrameworkCore.Uow;
using Abp.MultiTenancy;
using Microsoft.EntityFrameworkCore;

namespace YOUR_PROJECT_NAME_HERE.EntityFrameworkCore.Seed
{
    public static class MigrationHelper
    {
        public static void MigrateDb(IIocResolver iocResolver)
        {
            using (var uowManager = iocResolver.ResolveAsDisposable<IUnitOfWorkManager>())
            {
                using (var uow = uowManager.Object.Begin(new UnitOfWorkOptions() { IsTransactional = false }))
                {
                    var context = uowManager.Object.Current.GetDbContext<YOUR_PROJECT_DBCONTEXT_HERE>(MultiTenancySides.Host);

                    MigrateDb(context);

                    uow.Complete();
                }
            }
        }

        public static void MigrateDb(YOUR_PROJECT_DBCONTEXT_HERE context)
        {
            context.Database.Migrate();
            context.SaveChanges();
        }
    }
}
```

## Run helper on Entity Framework Modules PostInitialise Method

Add the following to your EF's PostInitialise()
```cs
    public override void PostInitialize()
    {
        MigrationHelper.MigrateDb(IocManager);
        if (!SkipDbSeed)
        {
            SeedHelper.SeedHostDb(IocManager);
        }
    }
```

# Done!

Now on startup the application will run its migrations

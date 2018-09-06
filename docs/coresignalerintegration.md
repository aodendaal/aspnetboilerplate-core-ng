# ASPNET Core SignalR Integration

For more information about ASPNET Core SignalR check out [SignalR ASPNET Core Integration](https://aspnetboilerplate.com/Pages/Documents/SignalR-AspNetCore-Integration).

## 1. Add SignalR to ABP

***If you are using the ABP starter template SignalR is already implemented and you can skip to step 2***

Follow the installation steps [here](https://aspnetboilerplate.com/Pages/Documents/SignalR-AspNetCore-Integration#installation)

## 2. Add Abp.AppFactory.Sync

* Add the [Abp.AppFactory.Sync Nuget Package]() to your Web.Core project

* Add Abp.AppFactory.Sync as a dependency to you WebCoreModule
```cs
[DependsOn( ...,
      typeof(Abp.AppFactory.Sync)]
public class ExampleWebCoreModule : AbpModule 
{ 
     ...
}
```

## 3. Add Abp.AppFactory.Interfaces

***If Abp.AppFactory.Interfaces 1.3.0 or greater is already included in your Application project then skip to step 4***

* Add the [Abp.AppFactory.Interfaces Nuget Package]() to your Application project

## 4. Add Abp.AppFactory.AsyncCrudAppServiceBase

***If Abp.AppFactory.AsyncCrudAppServiceBase is already included in your Application project then skip to step 4***

* Add the [Abp.AppFactory.AsyncCrudAppServiceBase Nuget Package]() to your Application project

## 5. Implement Sync on your Application Services 

* Inherit AsyncCrudAppServiceBase on all your crud AppServices

```cs
public class ExampleAppService : AsyncCrudAppServiceBase<Example, ExampleDto>
{

      public DataAppService(
            IRepository<Data, int> repository,
            ISyncHub syncHub,
            ...
            ) : base(repository, syncHub)
      {
            ...
      }
      ...
}
```

* If overriding Create, Update or Delete methods be sure to either call the base method or call Sync() when you update your entities

```cs
        public override Task<ExampleDto> Update(ExampleDto input)
        {
            ...
            return base.Update(input);
        }
        
        /// OR
        
        public override async Task Delete(EntityDto<int> input)
        {
            ...
            await Sync();
        }
```

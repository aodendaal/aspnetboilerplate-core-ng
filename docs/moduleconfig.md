# Reading Module Configuration From AppSettings

Sometimes a module will require configuration settings that are best kept in an easy to edit file rather than being hard-coded. \.NET apps typically uses __app.config__ or __web.config__ and ABP uses __appsettings.json__ found in the __.Web.Host__ project.

We can add extra options to the settings file and retrieve them when our module is being initialized.

__Microsoft.Extensions.Configuration__ is an API for accessing Key/Value-based configuration settings in an application. It has many providers to read from: in-memory .NET objects, INI files, JSON files, XML files, command-line arguments, environment variables, an encrypted user store, and you can create your own custom provider.

The __.Core__ project provides the wrapper called __AppConfigurations__ which implements the API and accesses the settings file, but for modules not referencing the core project (i.e. infrastructure layer modules) we can still use the API and access the file ourselves.

## Initialize Configuration Using Wrapper

Add a project reference to the __.Core__ project.

```csharp
private readonly IConfigurationRoot _appConfiguration

public imfundoplatformWebCoreModule(IHostingEnvironment env)
{
    _appConfiguration = AppConfigurations.Get(env.ContentRootPath, env.EnvironmentName, env.IsDevelopment());
}
```

## Initialzie Configuration Using API

Using NuGet add a reference to __Microsoft.Extensions.Configuration.JSON__.

```csharp
private readonly IHostingEnvironment env;
private IConfigurationRoot _appConfiguration

public SendGridProviderModule(IHostingEnvironment env)
{
    this.env = env;

public override void PreInitialize()
{
    var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: true, reloadOnChange: true)
    _appConfiguration = builder.Build();
}
```

## Reading Settings
Below you can see we updated the __appsettings.json__ file and inserted a _SendGridProvider_ section between the ConnectionStrings and Authentication sections.

```json
  "ConnectionStrings": {
    "Default": "Data Source=(localdb)\\MSSQLLocalDB; Initial Catalog=SchoolPlatform;"
  },
  "SendGridProvider": {
    "APIKey": "SG.gzm0hRaHQKmY_AAAAAAAAA.ErEQxf_55555555Xh4qL80FcQAKrFmK2CHBwABXXXXX"
  },
  "Authentication": {
    "Facebook": {
      "IsEnabled": "false",
      "AppId": "",
      "AppSecret": ""
    },
```

With the ___appConfiguration__ object initialized we can access the settings in our _PreInitialize()_ or _Initialize()_ functions of our module.

```csharp
var key = _appConfiguration["SendGridProvider:APIKey"];
```

## Further Reading
* [Essential .NET - Configuration in .NET Core](https://msdn.microsoft.com/en-us/magazine/mt632279.aspx)

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Project Architecture](projectarchitecture.md)
* [Adding Email Verification](emailverification.md)
# Social Login

The [documentation](https://aspnetboilerplate.com/Pages/Documents/Zero/User-Management#social-logins) for version 3.8.3 for social media login is extremely vague, merely pointing developers to the Microsoft documentation. This article will try to answer the question of enabling social media for ABP directly.

## Facebook

## Google
To enable authentication via Google we must add the **Microsoft.AspNetCore.Authenticateion.Google** package to the **.Web.Host** project. 

```dotnet add package Microsoft.AspNetCore.Authentication.Google```

Then, in **AuthConfigurer.cs** in the **Configure** function add:

```csharp
if (bool.Parse(_appConfiguration["Authentication:Google:IsEnabled"]))
{
    services.AddAuthentication().AddGoogle(googleOptions =>
    {
        googleOptions.ClientId = _appConfiguration["Authentication:Google:ClientId"];
        googleOptions.ClientSecret = _appConfiguration["Authentication:Google:ClientSecret"];
    });
}
```

## Twitter

## See Also
* [Writing to the server log file](serverlog.md)
* [Creating a Custom Repository](customrepos.md)
* [User Manager, Roles & Permissions](docs/usermanager.md)

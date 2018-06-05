# Server Log File

## Writing to the server log

AbpServiceBase (which is inherited by **AppService** and **DomainService**) contains a property called **Logger** which can be used to write to the server logs (normally found in **.Web.Host**\App_Data\Logs\Logs.txt).

Call ```Logger.Debug()``` (or which ever level of verbosity you require i.e. ```Info```, ```Debug```, ```Warning```, ```Error``` or ```Fatal```) to log a message to the logfile.

```csharp
    public void DoSomething()
    {
        Logger.Debug("Something happened");
    }
```


## Accessing the server log from Azure
The server log can be accessed directly in the browser from the following URL:

https://**\<server>**.scm.azurewebsites.net/api/vfs/site/wwwroot/App_Data/Logs/Logs.txt

Substitute ```<server>``` for your web app name.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Deploying to Azure](deployment.md)
* [Using Docker to deploy to Azure](docker212.md)

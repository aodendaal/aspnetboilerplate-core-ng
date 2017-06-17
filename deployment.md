[< Back to tutorial](README.md)
# Deploying to Azure

This article describes how to deploy ASP\.NET Boilerplate Core & Angular to Microsoft Azure.

## Two Site Deployment

### App Service Config
Enable CORS on the server AppService.

### Build Angular Project
Run ```npm run ng build```

### Create web.config
Create a __web.config__ file in the newly created __/dist__ directory in __/angular__. Populate with config file with the code below. This will allow Angular routing.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.webServer>
    <staticContent>
      <remove fileExtension=".json" />
      <mimeMap fileExtension=".json" mimeType="application/json" />
	  <mimeMap fileExtension=".woff" mimeType="application/x-font-woff" />
	  <mimeMap fileExtension=".woff2" mimeType="application/x-font-woff" />
    </staticContent>
        <rewrite>
          <rules>
            <rule name="Routes" stopProcessing="true">
              <match url=".*" />
              <conditions logicalGrouping="MatchAll">
                <add input="{REQUEST_FILENAME}" matchType="IsFile" negate="true" />
                <add input="{REQUEST_FILENAME}" matchType="IsDirectory" negate="true" />
                <add input="{REQUEST_URI}" pattern="^/(api)" negate="true" />
              </conditions>
              <action type="Rewrite" url="/" />
            </rule>
          </rules>
        </rewrite>  
  </system.webServer>
</configuration>
```

### FTP to App Service

## One Site Deployment - UNTESTED
* Merge Solutions
* Deploy Frontend
* Deploy Backend
* Deploy Database
* Setup VSTS build automation

### Merge Solutions
[ASP\.NET Zero article](https://www.aspnetzero.com/Documents/Merge-Angular-Client-Server)

### Deploy Frontend
* Run ```npm run ng build```
* FTP to server

### Deploy Backend
* Publish using Visual Studio 2017

### Deploy Database
* Update appsettings.json connection string
* Use .NET Core CLI

### Setup VSTS build automation

[< Back to tutorial](README.md)
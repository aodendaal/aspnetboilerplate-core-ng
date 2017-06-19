[< Back to tutorial](README.md)
# Deploying to Azure

This article describes how to deploy ASP\.NET Boilerplate Core & Angular to Microsoft Azure.

* Two Site Deployment
* One Site Deployment

## Two Site Deployment
This solution uses two different AppServices (one for the backend and one for the frontend) and a SQL database.

* __Backend__
  * \1. Create server App Service & Database
  * \2. Create publish profile in Visual Studio 2017
  * \3. Update Startup for CORS
  * \4. Update Connection Strings
  * \5. Publish from Visual Studio 2017
* __Frontend__
  * \1. Create client App Service
  * \2. Enable CORS on server App Service
  * \3. Update appconfig.json
  * \4. Build Angular project
  * \5. Create web.config
  * \6. FTP to App Service

### Backend
TODO

### Frontend
Now let's upload the Angular project to Azure.

#### 1. Create client App Service
TODO

#### 2. Enable CORS App Service Config
Enable CORS on the server AppService.

#### 3. Update appconfig.json
Edit __/angular/src/appconfig.json__ and set ```remoteServiceBaseUrl``` and ```appBaseUrl```.

#### 4. Build Angular Project
Run ```npm run ng build``` to create a distribution of the Angular project.

#### 5. Create web.config
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

#### 6. FTP to App Service
TODO

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
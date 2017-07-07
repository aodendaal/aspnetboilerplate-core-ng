# Deploying to Azure
This article describes how to deploy ASP\.NET Boilerplate Core & Angular to Microsoft Azure; as well as how to troubleshoot typical issues.

## One Site Deployment
It's technically possible to merge the angular site and ASP\.NET Core site together into a single solution. The process has been described in an [ASP\.NET Zero article](https://www.aspnetzero.com/Documents/Merge-Angular-Client-Server).

## Two Site Deployment
Possibly an easier process is a two site deployment with two different AppServices (one for the backend and one for the frontend) and a SQL database.

1. __Backend__
  1.1. Create server App Service & Database
  1.2. Create publish profile in Visual Studio 2017
  1.3. Update Startup for CORS
  1.4. Update Connection Strings
  1.5. Publish from Visual Studio 2017
  1.6. Run database update
2. __Frontend__
  2.1. Create client App Service
  2.2. Enable CORS on server App Service
  2.3. Update appconfig.json
  2.4. Build Angular project
  2.5. Create web.config
  2.6. FTP to App Service

### Backend

#### 1.vi. Run database update
Unfortunately you must manually run the database updates on the server. Luckily, we can use the EF CLI in the .EntityFrameworkCore project to update the server.

### Frontend
Now let's upload the Angular project to Azure.

#### 2.ii. Enable CORS App Service Config
Enable CORS on the server AppService.

#### 2.iii. Update appconfig.json
Edit __/angular/src/assets/appconfig.json__ and set ```remoteServiceBaseUrl``` and ```appBaseUrl```.

#### 2.iv. Build Angular Project
Run ```npm run ng build``` to create a distribution of the Angular project.

#### 2.v. Create web.config
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

## Troubleshooting

![A useless error message](img/uselesserror.png "A useless error message")

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [How to Initialize and Run a Clean Template](cleantemplate.md)
* [Adding Email Verification using SendGrid](emailverification.md)
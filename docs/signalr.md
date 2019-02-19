# Using SignalR

On the client, SignalR is configured in the helper **SignalRAspNetCoreHelper** and Angular components use the ABP Event Bus to send and receive messages from the server.

Below we will implement the example provided by the ABP documentation.

## Server-side
Create your SignalR hubs in the **.Web.Core** project. Based on the example from the [documentation](https://aspnetboilerplate.com/Pages/Documents/SignalR-AspNetCore-Integration) create a folder in **.Web.Core** called *Hubs*. Create a new class called *MyChatHub*. Replace the new class with the code from the example.

## Client-side
Update **/shared/helpers/SignalRAspNetCoreHelper.ts** and replace 

```javascript
jQuery.getScript(AppConsts.appBaseUrl + '/assets/abp/abp.signalr-client.js');
```

with

```javascript
jQuery.getScript(AppConsts.appBaseUrl + '/assets/abp/abp.signalr-client.js', () => {
    this.setupMyChatHub();
});
```

then add a new `static` Functions

```javascript
static setupMyChatHub(): void {
    var chatHub = null;

    abp.signalr.startConnection(abp.appPath + 'signalr-myChatHub', function (connection) {
        chatHub = connection; // Save a reference to the hub
        connection.on('getMessage', function (message) { // Register for incoming messages
            abp.event.trigger('myChatHub.getMessage', message);
        });
    }).then(function (connection) {
        abp.log.debug('Connected to myChatHub server!');
        abp.event.trigger('myChatHub.connected');
    });

    abp.event.on('myChatHub.connected', function () { // Register for connect event
        chatHub.invoke('sendMessage', "Hi everybody, I'm connected to the chat!"); // Send a message to the server
    });

    abp.event.on('myChatHub.sendMessage', (message) => {
        chatHub.invoke('sendMessage', message);
    });
}
```

The convention is to create events with the hub name and method name *[hubName].[methodName]*.

In your component:

```javascript
ngOnInit(): void {
    abp.event.on('myChatHub.getMessage', (message) => {
        this.messages.push(message);
    });
}

send(event: any) {
    abp.event.trigger('myChatHub.sendMessage', event.srcElement.value);
    event.srcElement.value = "";
}
```


## See Also
* [ASP\.NET Boilerplate Tutorials](readme.md)
* [Project Architecture](projectarchitecture.md)
* [Frontend Built-in Functions](angularbuiltin.md)
# Frontend Built-in Functions
These are functions provided by ABP for the Angular frontend.

* [ajax](#ajax)
* [toAbsAppPath](#toabsapppath)

#### [Auth](#auth-1)
* [areAllGranted](#areallgranted)
* [clearToken](#cleartoken)
* [getToken](#gettoken)
* [isAnyGranted](#isanygranted)
* [isGranted](#isgranted)
* [setToken](#settoken)

#### [Clock](#clock)
* [normalize](#normalize)
* [now](#now)

#### [Event](#event)
* [off](#off)
* [on](#on)
* [trigger](#trigger)

#### Features
* get
* getValue
* isEnabled

#### Localization
* getSource
* isCurrentCulture
* localize

#### [Log](#log-1)
* [debug](#debug)
* [error](#error)
* [fatal](#fatal)
* [info](#info)
* [log](#log)
* [warn](#warn)

#### [Message](#message-1)
* [confirm](#confirm)
* [error](#error-1)
* [info](#info-1)
* [success](#success)
* [warn](#warn-1)

#### MultiTenancy
* getTenantIdCookie
* setTenantIdCookie

#### Nav
_none_

#### Notifications
* getFormattedMessageFromUserNotification
* getUiNotifyFuncBySeverity
* getUserNotificationStateAsString
* showUiNotifyForUserNotification

#### [Notify](#notify-1)
* [error](#error-2)
* [info](#info-2)
* [success](#success-1)
* [warn](#warn-2)

#### Security
* [antiForgery.getToken](#antiforgerygetoken)

#### Setting
* get
* getBoolean
* getInt

#### SignalR
* connect

#### Timing
* convertToUserTimezone

#### UI
* block
* clearBusy
* setBusy
* unblock

#### Utils
* buildQueryString
* createNamespace
* deleteCookie
* formatString
* [getCookieValue](#getCookieValue)
* isFunction
* replaceAll
* [setCookieValue](#setCookieValue)
* toCamelCase
* toPascalCase
* truncateString
* truncateStringWithPostfix

## _root_
### ajax
Used to call server-side services using AJAX and evaluate the return value. Since ASP.NET Boilerplate server-side code returns a standard response for AJAX calls, it's suggested to use this method to handle the standard return value.

### toAbsAppPath

## Auth

### areAllGranted
```abp.auth.areAllGranted(...args: string[]): boolean;```

### clearToken
```abp.auth.clearToken(): void;```

### getToken
```abp.auth.getToken(): string;```

### isAnyGranted
```abp.auth.isAnyGranted(...args: string[]): boolean;```

### isGranted
```abp.isGranted(permissionName: string): boolean;```

### setToken
```abp.auth.setToken(authToken: string, expireDate?: Date): void;```
Saves auth token.

## Clock

### normalize
```normalize(date: Date): Date;```

### now
```now(): Date;```

## Event
Used to register to and trigger client side global events.

## Log

### debug
```abp.log.debug(logObject?: any): void;```

### error
```abp.log.error(logObject?: any): void;```

### fatal
```abp.log.fatal(logObject?: any): void;```

### info
```abp.log.info(logObject?: any): void;```

### log
```abp.log.log(logObject?: any, logLevel?: levels): void;```

### warn
```abp.log.warn(logObject?: any): void;```

## Message

### confirm
```abp.message.confirm(message: string, callback?: (result: boolean) => void): Promise;```

```abp.message.confirm(message: string, title?: string, callback?: (result: boolean) => void): Promise;```

### error
```abp.message.error(message: string, title?: string): Promise;```

### info
```abp.message.info(message: string, title?: string): Promise;```

![info dialog](/img/infomessage.png "info dialog")

### success
```abp.message.success(message: string, title?: string): Promise;```

### warn
```abp.message.warn(message: string, title?: string): Promise;```

## Notify
Used to show auto-disappearing notifications.

Generate a pop-up notification in the bottom-right corner that doesn't prevent the user from using the rest of the system. After a short time the notification fades away.

Multiple notifications above each other and can be clicked on to make them fade immediately.

### error
```abp.notify.error(message: string, title?: string, options?: any): void;```

Generates an error notification

### info
```abp.notify.info(message: string, title?: string, options?: any): void;```

Generates an information notification

![info notification](/img/infonotification.png "info notification")

### success
```success(message: string, title?: string, options?: any): void;```

Generates a success notification

### warn
```abp.notify.warn(message: string, title?: string, options?: any): void;```

Generates a warning notification

## UI
Used to make an area (a div, a form, entire page...) blocked for user inputs. Also used to make an area busy (with a busy indicator).

### block
Adds a transparent overlay to the document or element so the user cannot interact with it.

### clearBusy
Removes the busy overlay from the document or element.

### setBusy
Adds a semi-transparent overlay with a busy indicator to the document or element and prevents the user from interacting with the document or element.

### unblock
Removes the transparent overlay from the document or element.

## Utils

### formatString
Similar to ```string.Format``` in C#

### getCookieValue
```abp.utils.getCookieValue(key: string): string;```

Gets a cookie with given key.
This is a simple implementation created to be used by ABP.
Please use a complete cookie library if you need.

### setCookieValue
```abp.utils.setCookieValue(key: string, value: string, expireDate?: Date, path?: string): void;```

Sets a cookie value for given key.
This is a simple implementation created to be used by ABP.
Please use a complete cookie library if you need.

## See Also
* [ASP\.NET Boilerplate Tutorials](readme.md)
* [Creating Modal Dialogs](modals.md)
* [Project Architecture](projectarchitecture.md)
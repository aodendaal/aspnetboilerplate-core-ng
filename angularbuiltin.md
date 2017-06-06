[< Back to tutorial](README.md)

# Frontend Built-in Functions

#### [Auth](#auth-1)
* [clearToken](#cleartoken)
* [getToken](#gettoken)
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
* [error](#error)
* [info](#info)
* [success](#success)
* [warn](#warn)

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

#### Notify
* error
* info
* success
* warn

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

## Auth

### clearToken
```abp.auth.clearToken(): void;```

### getToken
```abp.auth.getToken(): string;```

### setToken
```abp.auth.setToken(authToken: string, expireDate?: Date): void;```
Saves auth token.

## Clock

### normalize
```normalize(date: Date): Date;```

### now
```now(): Date;```

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

![info dialog](img/infomessage.png "info dialog")

### success
```abp.message.success(message: string, title?: string): Promise;```

### warn
```abp.message.warn(message: string, title?: string): Promise;```

## Notify

### info
```abp.notify.info(message: string, title?: string, options?: any): void;```

![info notification](img/infonotification.png "info notification")

## Utils

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

[< Back to tutorial](README.md)
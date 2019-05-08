# Throwing HTTP Error Codes
An application service is separated from the technology hosting the service but by throwing the right exception the correct HTTP status will be returned when hosting it as a REST service.

This default functionality can be overridden by creating an ExceptionFilter and registering it. TODO

## 400 - Bad Request
Throw **AbpValidationException**

## 401 - Unauthorized
Throwing **AbpAuthorizationException** will return Unauthorized if there's a session user.

## 403 - Forbidden
Throwing **AbpAuthorizationException** will return Forbidden if there's no session user.

## 404 - Not Found
Throw **EntityNotFoundException**

## See Also
* [How to Create an Application Service](docs/applicationservice.md)
* [Using Predefined Permissions](docs/permissions.md)
* [User Manager, Roles & Permissions](docs/usermanager.md)
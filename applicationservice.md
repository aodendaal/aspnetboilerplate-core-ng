[< Back to tutorial](README.md)

# Creating an Application Service
* [Unit of Work](#unit-of-work)
* [Hide from Controller](#hide-from-controller)

### Unit of Work
By default functions in an application service are transactional, meaning if there's an exception in the function then all repository functions are rolled back. It can be turned off by adding the ```UnitOfWork``` attribute to your function and setting ```IsDisabled``` to ```true```.
```csharp
[UnitOfWork(IsDisabled: true)]
```
### Hide from Controller
The __.Web.Core__ module is configured to generate WebAPI controllers for any application services found in __.Application__. To prevent a specific application service or function in a service from being generated, add the ```RemoteService``` attibute and set ```isEnabled``` to ```false```.
```csharp
[RemoteService(isEnabled: false)]
```

[< Back to tutorial](README.md)
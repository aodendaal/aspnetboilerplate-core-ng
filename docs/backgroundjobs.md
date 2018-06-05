# Background Jobs

For more information about Hangfire check out [Background Jobs with Hangfire](https://aspnetboilerplate.com/Pages/Documents/Hangfire-Integration). This article extends the information on top of the [official documentation](https://aspnetboilerplate.com/Pages/Documents/Background-Jobs-And-Workers).

## Requirements

If you're injecting dependencies, especially repositories, you will need to add the ```[UnitOfWork]``` attribute.

By default jobs run under the host tenant so you might have to surround your calls with ```using (CurrentUnitOfWork.SetTenantId())```
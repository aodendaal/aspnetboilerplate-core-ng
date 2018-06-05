# Including JavaScript libraries

Here is a good tutorial for including JavaScript libraries in Angular 
https://hackernoon.com/how-to-use-javascript-libraries-in-angular-2-apps-ff274ba601af

1. Add the package using ```yarn add```
2. 

## Include bootstrap-select
The theme **AdminBSB** has a [preview](https://gurayyarar.github.io/AdminBSBMaterialDesign/) which contains examples for an [advanced select](https://gurayyarar.github.io/AdminBSBMaterialDesign/pages/forms/advanced-form-elements.html) using `bootstrap-select` but if you try to implement the control you do not get the expected result. ABP version 3.4.1 includes `bootstrap-select` in the package dependencies (**package.json**) but it still needs to be manually added to the Angular CLI config (**.angular-cli.json**) to work properly.

Edit **.angular-cli.json** and add references to the bootstrap-select .css and .js files in the sections as shown below:

```typescript
{
  ...
  "apps": [
    {
      ...
      "styles": [
        ...
        "../node_modules/bootstrap-select/dist/css/bootstrap-select.min.css",
        ...
      ],
      "scripts": [
        ...
        "../node_modules/bootstrap-select/dist/js/bootstrap-select.min.js",
        ...
      ],
      ...
    }
  ],
  ...
}
```

Now you can use the `data-` attributes as demonstrated in the theme's preview examples.

## See Also
* [ASP\.NET Boilerplate Tutorials](README.md)
* [Creating modal dialogs](modals.md)
* [Read URL query parameters](routing.md)
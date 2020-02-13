# AngularHexa

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 9.0.0-rc.12.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The app will automatically reload if you change any of the source files.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory. Use the `--prod` flag for a production build.

## Running unit tests

Run `ng test` to execute the unit tests via [Karma](https://karma-runner.github.io).

## Running end-to-end tests

Run `ng e2e` to execute the end-to-end tests via [Protractor](http://www.protractortest.org/).

## Deploy to Azure

- Run `npm run hexa:init` on local machine and follow Hexa's instructions. This will create a `hexa.json`
- Commit your changes.
- Run `npm run hexa:ci` on local machine, this will print the following credentials:
```
{
  appId: 'xx4362xx-aaxx-40xx-8bxx-xx6ea0c351xx',
  displayName: 'appname',
  name: 'http://appname',
  password: 'xxce72xx-1axx-44xx-81xx-35xxb15xxa1e',
  tenant: 'xxf988xx-86xx-41xx-91xx-2d7cd011dbxx'
}
```
- Configure your CI with the following environment variables (secrets):
`AZURE_SERVICE_PRINCIPAL_ID`: the appId from the service principal config.
`AZURE_SERVICE_PRINCIPAL_PASSWORD`: the password from the service principal config.
`AZURE_SERVICE_PRINCIPAL_TENANT`: The tenant from the service principal config.

## Further help

To get more help on the Angular CLI use `ng help` or go check out the [Angular CLI README](https://github.com/angular/angular-cli/blob/master/README.md).

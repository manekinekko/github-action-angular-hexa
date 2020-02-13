# ![Deploy to Azure with Hexa.run](https://github.com/manekinekko/github-action-angular-hexa/workflows/Deploy%20to%20Azure%20with%20Hexa.run/badge.svg)

## Deploy Angular to Azure with [Hexa.run](https://hexa.run)

### On your local machine

- Run `npm run hexa:login` to log into your Azure account.
- Run `npm run hexa:init` and follow Hexa's instructions. This will create a `hexa.json`.
  - NOTE: the hosting public folder should point to `./dist/angular-app-name/`
- Commit your changes.
- Run `npm run hexa:ci`, this will print the following credentials:
```
{
  appId: 'xx4362xx-aaxx-40xx-8bxx-xx6ea0c351xx',
  displayName: 'appname',
  name: 'http://appname',
  password: 'xxce72xx-1axx-44xx-81xx-35xxb15xxa1e',
  tenant: 'xxf988xx-86xx-41xx-91xx-2d7cd011dbxx'
}
```

### On the CI
- Configure your CI with the following environment variables (secrets):
`AZURE_SERVICE_PRINCIPAL_ID`: the appId from the service principal config.
`AZURE_SERVICE_PRINCIPAL_PASSWORD`: the password from the service principal config.
`AZURE_SERVICE_PRINCIPAL_TENANT`: The tenant from the service principal config.
- On your workflow, run the following sequence (in this order):
1. `npm run hexa:login` (this will login to Azure using your secrets)
1. `npm run build -- --prod` this will build your Angular app in production mode.
1. `npm run hexa:deploy` this will initiate the deploy process to your Azure storage and prints out the URL to your application, which looks like `➜ Hosting: https://xxxx.yy.web.core.windows.net`



# ![Deploy to Azure with Hexa.run](https://github.com/manekinekko/github-action-angular-hexa/workflows/Deploy%20to%20Azure%20with%20Hexa.run/badge.svg)

## Deploy Angular to Azure with [Hexa.run](https://hexa.run)

<p align="center">
  <img src="https://github.com/manekinekko/github-action-angular-hexa/raw/master/src/assets/angular-hexa-deploy-to-azure.png"/>
</p>


### 1/ Install the Hexa.run CLI

Inside your Angular project make sure to install the Hexa.run CLI as a prod dependency `npm i -S @manekinekko/hexa` as you can see from the [package.json](https://github.com/manekinekko/github-action-angular-hexa/blob/master/package.json#L29) of this project. 

### 2/ Add your NPM aliases (optional)
The `npm run heax:...` commands mentioned below are just aliases to the Hexa cli ( [see the package.json example file](https://github.com/manekinekko/github-action-angular-hexa/blob/master/package.json#L11-L17) ). You will have to add them to your own `package.json` or use your own aliases.

### 3/ On your local machine

- Install the Hexa.run CLI: `npm i -S @manekinekko/hexa`
- Log into your Azure account: `npm run hexa:login`
- Run the Hexa CLI and follow the instructions: `npm run hexa:init`.
  - NOTE: the hosting public folder should point to `./dist/angular-app-name/`
- Hexa will create a `hexa.json` (you need to version it to git).
- Commit your changes.
- Run `npm run hexa:ci`, and write down the following credentials (you will need them later):
```
{
  appId: 'xx4362xx-aaxx-40xx-8bxx-xx6ea0c351xx',
  displayName: 'appname',
  name: 'http://appname',
  password: 'xxce72xx-1axx-44xx-81xx-35xxb15xxa1e',
  tenant: 'xxf988xx-86xx-41xx-91xx-2d7cd011dbxx'
}
```

### 4/ On the CI
- Configure your CI with the following environment variables (secrets):
`AZURE_SERVICE_PRINCIPAL_ID`: the appId from the service principal config.
`AZURE_SERVICE_PRINCIPAL_PASSWORD`: the password from the service principal config.
`AZURE_SERVICE_PRINCIPAL_TENANT`: The tenant from the service principal config.
- On your workflow, run the following sequence (in this order):
1. `npm run hexa:login` (this will login to Azure using your secrets)
1. `npm run build -- --prod` this will build your Angular app in production mode.
1. `npm run hexa:deploy` this will initiate the deploy process to your Azure storage and prints out the URL to your application, which looks like `➜ Hosting: https://xxxx.yy.web.core.windows.net`
1. Enjoy your newly deployed Angular application 🎉

### Notes

When it comes to hosting your static application on Azure, Hexa.run will automatically:
1. create an Azure resource group (or lets you choose an existing one) 
2. create the Azure storage account 
3. configure the storage account and make it `static-website` ready
4. upload the angular bundle.
5. prints the generated URL from the Azure service.

Hexa can also deploy your Azure Functions, Table Storage or Cosmos DB, etc. ([read me](https://hexa.run)).

Don't have an Azure account? [Create one for free](azure.microsoft.com/free/?WT.mc_id=hexa-github-wachegha) and get started with 12 months of free services.

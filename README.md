# Azure Functions Template

A template for getting started with Azure Functions using C#.

## Prerequisites

See <https://docs.microsoft.com/en-us/azure/azure-functions/create-first-function-cli-csharp>.

* .Net 5 SDK
* The [Azure Functions Core Tools](https://docs.microsoft.com/en-us/azure/azure-functions/functions-run-local) version 3.x.
* Azure CLI
* Visual Studio Code

### Creat a new function project

This is intended as a template api but it is not ready for production just yet!

Create the function project

```sh
func init Template.FunctionApp --dotnet
cd Template.FunctionApp/
code .
```

Add a function

```sh
func new --name HttpExample --template "HTTP trigger" --authlevel "anonymous"
```

Run the function locally

```sh
func start
```

The local URL that the function will be running on will be displayed. Eg <http://localhost:7071/api/HttpExample>.

## Create the Azure resources for the Function App

We will use bicep to create as infrastructure as code.

See <https://github.com/Azure/bicep/blob/main/docs/examples/101/function-app-create/main.bicep>.

### Deploy the Bicep template from local

Added default values to the template when running local.

```sh
deploymentName=AzureFunctionsQuickstart
resourceGroupName=AzureFunctionsQuickstart-rg
location=australiaeast
az group create -l $location -n $resourceGroupName
az deployment group create \
  --name $deploymentName \
  --resource-group $resourceGroupName \
  --template-file "./Infrastructure/FunctionApp/main.bicep" \
  --parameters "./Infrastructure/FunctionApp/main.parameters.dev.json"
```

## Deploy the function project to Azure

```sh
cd Template.FunctionApp/
func azure functionapp publish <APP_NAME>
```

The URL that the function will be running on will be displayed.

View near real-time logs

```sh
func azure functionapp logstream <APP_NAME>
```

## Clean up deployment

```sh
resourceGroupName={resource group name}
az group delete --name $resourceGroupName --yes --no-wait
```

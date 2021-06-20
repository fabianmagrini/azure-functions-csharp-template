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

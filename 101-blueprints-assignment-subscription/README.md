# Azure Blueprints - assign definition

<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2FDCtheGeek%2Fazure-quickstart-templates%2Fdmc-bp-assignment%2F101-blueprints-assignment-subscription%2Fazuredeploy.json" target="_blank">
    <img src="http://azuredeploy.net/deploybutton.png"/>
</a>
<a href="http://armviz.io/#/?load=https%3A%2F%2Fraw.githubusercontent.com%2FDCtheGeek%2Fazure-quickstart-templates%2Fdmc-bp-assignment%2F101-blueprints-assignment-subscription%2Fazuredeploy.json" target="_blank">
    <img src="http://armviz.io/visualizebutton.png"/>
</a>

This template assigns an existing Azure Blueprints definition with api-version 2018-11-01-preview.

The [101-blueprints-definition-subscription](../101-blueprints-definition-subscription/) template
should be run first so that the target blueprint exists in your subscription.

## General template parameters

The following parameters are used to specify the blueprint definition to deploy:

- blueprintName: The name of the blueprint saved in the subscription to assign. Default value is _101-blueprint-definition-subscription_.
- blueprintVersion: The version of the blueprint to assign. Default value is _1.0_.
- subscriptionId: The subscription to assign the blueprint to. Default value is _[subscription().id]_, a function to get the current subscription ID.

## Blueprint artifacts and parameters

The following blueprint artifacts comprise the definition this template matches:

|Type |Name |Parameters |Description |
|-|-|-|-|
|Resource group |FirstRG |resourceGroupName and resourceGroupLocation |Creates a resource group with the provided name and location in the subscription. Default name value is _BlueprintCreatedRG_ and location value is _westus2_. |
|\- Policy assignment |Allowed locations |policyLocation |Deploys the [Azure Policy - Allowed locations](https://docs.microsoft.com/azure/governance/policy/samples/allowed-locations) definition. The parameter values are passed to the policy assignment. Default value is _eastus2;westus;westus_.|
|\- Role assignment |Reader |roleAssignedTo |Assigns the _Reader_ role to the account provided in the parameter. No default value.|
|\- Resource Manager template |StorageAccount |templateStorageAccountType |Deploys the [101-storage-account-create](https://github.com/Azure/azure-quickstart-templates/tree/master/101-storage-account-create) Azure QuickStart template using the passed parameter. Default value is _Standard\_LRS_. |

## Next steps

Check out the [Azure Blueprints](https://docs.microsoft.com/azure/governance/blueprints/overview)
for more information on how to use Blueprints to manage your environment.
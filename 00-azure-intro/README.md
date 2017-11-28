# Azure Introduction

This setup document covers many pre-requisites for running Docker EE demonstrations on Azure-based infrastructure.

## Vocabulary

Culled from the [Azure Docs](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#terminology):

| Concept | Description |
| --- | --- |
| [Resource Groups](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#resource-groups) | A container that holds related resources for an Azure solution. The resource group can include all the resources for the solution, or only those resources that you want to manage as a group. You decide how you want to allocate resources to resource groups based on what makes the most sense for your organization |
| Resource | A manageable item that is available through Azure. Some common resources are a virtual machine, storage account, web app, database, and virtual network, but there are many more. |
| [Azure Resource Manager (ARM) Template](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-overview#template-deployment) | A JavaScript Object Notation (JSON) file that defines one or more resources to deploy to a resource group. It also defines the dependencies between the deployed resources. The template can be used to deploy the resources consistently and repeatedly. Roughly analagous to AWS Cloud Formation templates. |
| [Service Principal](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-application-objects) | Service account that is assigned specific permissions (ex. create resources) to either the Subscription, Resource Group, or individual resources. Used to automate management of Azure resources, ex. Docker EE for Azure uses a service principal to open and close ports on a load balancer based on Docker Services' published ports. Part of the Azure Active Directory (AAD) resource. |

## Options

### Docker EE for Azure

Docker has created a formal Edition known as [Docker EE for Azure](https://docs.docker.com/docker-for-azure/why/). EE for Azure is an ARM Template distributed through the Azure Marketplace that both provisions Azure infrastructure and configures an EE cluster (DTR + UCP).

Pros
* Simple setup - kickoff the template and in 20 minutes you're ready to roll
* Requires zero Azure knowledge - create template, get UCP URL, demonstrate
* Scalable worker nodes - click a button and can scale in/out in minutes

Cons
* Requires setup of a Service Principal
* Base OS is a custom Moby build that has shown instability
* If you scale your manager nodes, you're going to have a bad time

### Roll your own

While Docker EE for Azure is a fully automated experience and great for quick demonstrations, many customers report enough instability to warrant a custom EE implementation. In this approach, Docker EE is deployed on Azure infrastructure without the formal edition template; instead, virtual machines (or better - [Virtual Machine Scale Sets](https://docs.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-overview)) are provisioned and EE installed.

Pros
* Complete control - do not have to rely on opinionated decisions made by EE for Azure
* OS options - customers that have a specific blessed OS often want to see EE on that OS rather than Moby

Cons
* Everything is manual - there are a few ARM Templates that provide automation, but nothing as robust as the EE for Azure Edition
* Requires more knowledge of Azure to be successful

## Azure Portal

Most users' first experience with Azure is the [Azure Portal](https://portal.azure.com). It is a browser-based web application that contains an exhaustive array of management screens for Azure resources. 

There is also a [mobile application](https://azure.microsoft.com/en-us/features/azure-portal/mobile-app/) that can be used to manage Azure resources.

## Azure Command Line Interface (CLI)

Azure has a well-regarded CLI for managing the lifecycle of Azure Resources. [Install](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest#a-namemacosinstall-on-macos) the CLI for your particular operating system and [login](https://docs.microsoft.com/en-us/cli/azure/authenticate-azure-cli?view=azure-cli-latest#interactive-log-in) to your account by running `az login`. 

A capable alternative is the [Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview) integrated into the Azure Portal.

## Resources

| Resource | Description |
| --- | --- |
| [Azure Documentation](https://docs.microsoft.com/en-us/azure/) | Exhaustive, reguarly updated documentation on the Azure ecosystem. Quality varies from resource to resource, but in general is a great place to dig into technical specifics. Often includes step by step tutorials and quickstarts for a given topic |
| [Quickstart Templates Repo](https://github.com/Azure/azure-quickstart-templates) | GitHub repository containing hundreds of ARM Templates for various deployments. Is a great starting point for building out templates, as most scenarios are covered and can be copied/pasted into your own |
| [Azure Blog](https://azure.microsoft.com/en-us/blog/) | Regularly updated blog with an [RSS feed](https://azure.microsoft.com/en-us/blog/feed/) |
| [Azure Architecture Center](https://docs.microsoft.com/en-us/azure/architecture/) | Guidance for application design, reference architectures, best practices, and checklists |
| [Azure Storage Explorer](https://azure.microsoft.com/en-us/features/storage-explorer/) | GUI tool for interacting with data stored in Azure Storage Accounts (volumes, DTR storage, logs). |
| [Channel9](https://channel9.msdn.com/Azure) | Online video repository chalked full of Azure videos |
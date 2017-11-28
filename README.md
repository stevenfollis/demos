# Demonstrating Docker EE with the Windows Ecosystem

This repository is a collection of demonstration scripts and supporting files for showcasing the value of [Docker Enterprise Edition](https://www.docker.com/enterprise-edition) within the Windows ecosystem. 

## Demonstrations

| Demo | Status | Description |
| --- | --- | --- |
| [Azure Intro](./00-azure-intro) | Stable | Overview of Azure including EE deployment options |
| [Windows Containers Hello World](./01-hello-world) | Stable | Introduction to Windows Containers including simple demonstrations |
| [SQL Server](./02-sql) | To-Do | Running MSSQL workloads in Windows Containers |
| [Visual Studio Team Services](./03-vsts) | To-Do | Integrating CI/CD with Docker EE via [VSTS](https://www.visualstudio.com/team-services/) |
| [IOT Edge](./04-iot) | To-Do | Managing IOT Edge module containers with DTR |

## Windows Containers Differences

There are a variety of subtle differences between Windows and Linux containers to keep in mind:

* KB article: [What are known parities between Windows Server, Linux, and IBM Z Systems?](https://success.docker.com/article/What_are_known_parities_Windows_Linux_IBMZ)

* Ingress Routing Mesh support [is coming](https://blogs.technet.microsoft.com/virtualization/2017/09/26/dockers-ingress-routing-mesh-available-with-windows-server-version-1709/) but is not currently supported in Docker EE. To publish ports, use Host mode + DNS Round Robin
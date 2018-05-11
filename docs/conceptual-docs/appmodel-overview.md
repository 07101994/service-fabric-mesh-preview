# Service Fabric Applications

## Overview
Service Fabric Applications are the new, simple way to describe and deploy applications to everywhere Service Fabric runs, whether it's Mesh or your own clusters hosted in Azure, on prem, or on your laptop. 

Service Fabric Applications are a drastic departure from the ApplicationManifest and ServiceManifest Reliable Services XML model. With Service Fabric Applications, you no longer need to decide up front whether your service should be a Guest EXE, Guest Container, Enlighted Container, Reliable Service, etc. You simply write your application code like you normally would in any language or framework, describe how it should run in a simple YAML definition, and run it on Service Fabric. 


## How it works

Service Fabric Applications are based on **resources**. Each resource is a type of thing that can be deployed independently to Service Fabric, such as applications, services, network, volumes, or routing rules. Together, these resources compose a functioning application. 

Service Fabric currently supports the following resources:
- Application and services
- Networks
- Volumes

Additional resources will be available in the future, including:
- Secrets
- Traffic routing rules
- Auto-scale rules

### Application

An application resource is a collection of constituent services that perform a certain function or functions. The application resource acts as a grouping construct for services that should be deployed and upgraded together as a unit. The lifecycle of each application instance can be managed independently. For example, one application can be upgraded independently from other application. Typically, you keep the number of services in an application fairly small, as the more services you put into an application.

### Service

A service resource describes the containers and their configuration that you want to run. Each container and the resources   that you describe in the service resource is called a *code package*. Your service can contain multiple code packages. This set of code packages is a unit of deployment and activation, meaning that all code packages in the service will always be run together as a pod. All containers in the service share a namespace and can communicate with each other over localhost. 

Service can scale out by increasing its `replicaCount`. Scaling out would increase the number of running container instances for each code package.

Services can attach themselves to one or more network resources. All containers in that service will be able to communicate with any other services or external endpoints that are part of that network.

### Network

Use network resource to create private network and configure public connectivity for services within the application.

More than one service from different applications can be part of the same network.

### Volume

Use volume resource to define properties for a volume that needs to be mounted inside the container of a service.

## Examples

Following is the list of examples that shows how to achieve a particular scenario using Service Fabric Application Model v2. 

|Example Name|Scenario Description|
|------------|--------------------|
| [Hello World Mesh](./appmodel-scenarios-helloworld.md) | Learn about how to deploy a single container microservices application and connect to the service endpoint. |
| [Private  Registry](./appmodel-scenarios-private-registry.md) | Learn about how to use container images from a private registry. |
| [Azure File Volume](./appmodel-scenarios-azurefiles-volume.md) | Learn about how to store data on Azure Files. |
| [Complete Quickstart](./application-deployment-quickstart.md) | Learn about how to create an application with a frontend and backend service that uses DNS-based resolution. |

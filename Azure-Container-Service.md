Microsoft Azure Container Service makes it simpler for you to create, configure, and manage a cluster of virtual machines that are preconfigured to run containerized applications. It uses an optimized configuration of popular open-source scheduling and orchestration tools. This enables you to use your existing skills, or draw upon a large and growing body of community expertise, to deploy and manage container-based applications on Microsoft Azure.

![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/ec281d1f2161acc665bf4cb9dca1b64a/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M2L3T6_vgEaOWr.png)

Azure Container Service leverages the Docker container format to ensure that your application containers are fully portable. It also supports your choice of Marathon and DC/OS, Docker Swarm, or Kubernetes so that you can scale these applications to thousands of containers, or even tens of thousands.

By using Azure Container Service, you can take advantage of the enterprise-grade features of Azure, while still maintaining application portability–including portability at the orchestration layers.

Azure Container Service can integrate with different container registries, including Azure Container Registry. This service allows you to store images for different types of container deployments like Swarm, DC/OS and Kubernetes and Azure services such as App Service, Batch and Service Fabric.

AKS, or Azure Container Service, is a new managed Kubernetes service that provides additional capabilities such as Azure Active Directory-based authentication, webhook support, and delete operations.

The creation of a managed Kubernetes cluster could be done by using the CLI:

`az aks create --resource-group myResourceGroup --name myCluster --node-count <number_of_nodes> --generate-ssh-keys`
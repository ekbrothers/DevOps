---

A Microsoft Azure resource group is a container that holds related resources for an application. The resource group could include all the resources for an application, or only those resources that are logically grouped together. You can decide how you want to allocate resources to resource groups based on what makes the most sense for your organization.

---


![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/6b7ff1798d5c2ee692a31e26aa9178f8/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M2L4T2_UYE73bz.png)
Screenshot of an Azure Resource Group diagram. In the Center, a Web App icon has three arrows pointing out towards the following three icons: Virtual Machines, Document Database, and SQL Database. A fourth arrow points out to a rectangle named Azure Storage, with a Blob Storage icon and a Queue Storage icon inside of it.

There are some important factors to consider when defining your resource group:

* All the resources in your group should share the same lifecycle. You will deploy, update, and delete them together. If one resource, such as a database server, needs to exist on a different deployment cycle, it should be in another resource group.
* Each resource can only exist in one resource group at a time.
* You can add or remove a resource to a resource group at any time.
* You can move a resource from one resource group to another group.
* A resource group can contain resources that reside in different regions.
* A resource group can be used to scope access control for administrative actions.
* A resource can be linked to a resource in another resource group when the two resources must interact with each other, but they do not share the same lifecycle (for example, multiple apps connecting to a database).
---
<mark> A **Container** is a standard unit of software that packages up code and all its dependencies so the application runs quickly and reliably from one computing environment to another. Application containers are ideal for application development and testing because they have the combination of instant startup, which comes from OS virtualization, and reliable execution, which comes from isolation and resource governance. </mark>

---

## Containers compared to VMs
When compared to Virtual Machines, containers are:
* **Secure** 
Isolate applications’ execution environments from one another, but share the underlying OS kernel<br>
* **Lightweight** Use far fewer resources than VMs by not requiring an OS per application<br>
* **Consistent** Allow developers to quickly iterate over a development project, because their environment and resource usage are consistent across systems. A containerized application that works on a developer's machine will work the same way on a production system. <br>
* **Quick** Start up almost immediately & can be packed far more densely on the same hardware and spun up and down en masse with far less effort and overhead


Containers also help you to create isolated and allocated resources. Both technologies have similarities in that they create isolated environments with separate resource control (memory and CPU, for example). However, containers, unlike VMs, don't run an entire operating system. While VMs utilize a hardware virtualization technology, containers virtualize the operating system and share the kernel of the host machine.

By using containers, you can package an application with its dependencies and configurations to run it in different environments without concerning yourself with the underlying layers of the operating system and the infrastructure. This enables faster creation of isolated environments as well as a flexibility to deploy and release instances of the same container.

Instant start and a small footprint also benefit cloud scenarios; applications can scale out quickly, and many more application instances can fit on a machine than if they were each in a virtual machine. This maximizes resource utilization.

![Containerization](https://d33wubrfki0l68.cloudfront.net/26a177ede4d7b032362289c6fccd448fc4a91174/eb693/images/docs/container_evolution.svg)

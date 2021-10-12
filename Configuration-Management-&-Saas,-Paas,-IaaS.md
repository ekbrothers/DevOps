---

**Configuration Management** is the management of the configuration of all environments for an application. Typically, configuration management is done in the form of scripts that are version controlled. 

---

* Less formal than traditional configuration management.

* Encapsulation of configuration in code is emphasized over formal documentation.

* Lighter weight, executable configurations that allow us to have configuration and environments as code.

Both Infrastructure as Code (IaC) and configuration as code fall under configuration management.

---

**Infrastructure of Code refers to creating and provisioning machines, whereas configuration as code refers to configuring components and software on the machines (such opening ports and installing software).**

---

### Benefits of Configuration Management
* **More maintainable**: Mmanage variables and secrets at multiple levels. Needed variables can be stored in a project and defined configuration variables can be scoped to a specific release definition or to a specific environment in a release definition. 

* **Fewer locations to update**: By storing configuration and app settings in a deployment tool, if settings change at a given time, you only need to update the settings in the deployment tool rather than in every possible file in which the setting is hard-coded. By storing them at the right scope, you do not have to update all the release definitions or environments in which they are used.

* **Fewer mistakes**: When you store the appropriate settings for each environment in the environment itself in the deployment tool, you won’t accidentally point to the development connection string when in production. The values for settings are siloed out per environment, making it difficult to actively mix up if you are using a deployment tool.

* **More secure**: When you have connection strings, passwords, or any other settings stored in plain text in a settings file (such as a web.config file), anyone who has access to the code can potentially access a database or machine. A deployment tool such as Visual Studio Team Services provides a rich permissions model that governs who can manage and use secrets at each scope.

* **More reliable**: By automating the process of transforming configurations through a deployment tool, you’ll be able to count on the transforms always happening during a deployment and setting the appropriate values.

## **Infrastructure as Code** 
IaC entails defining environments, including networks, servers, and other compute resources, as a text file (script or definition) that is checked into version control and used as the base source for creating or updating those environments. For instance, adding a new server should be done by editing a text file and running the release pipeline, not by remoting into the environment and spinning up one manually.
A common analogy for using Infrastructure as Code is the distinction between owning pets and cattle. When you own pets, you give them names, you treat them individually, and if something bad happens to them, you care a lot. If you have a herd of cattle, you might still name them, but you treat them as a herd. In infrastructure terms, without treating environments as code, there might be severe implications if a machine crashes and you need to replace it (pets). If you use Infrastructure as Code, if a machine goes down, you can just spin up another machine with no issues (cattle).

When designing scripts or definitions for Infrastructure as Code (IaC), it’s important to make sure that the code and tools are set up to be idempotent, or able to run multiple times without error and with consistency.

Infrastructure as Code can also be set up with developers' help because many tools offer the ability to write code in familiar programming languages, even ones as simple as JavaScript Object Notification (JSON) definitions. Some examples of common tools you use can to work with Infrastructure as Code are Vagrant, Ansible, Puppet, Chef, Docker, Microsoft Windows PowerShell DSC, and cloud-provided tools such as Azure Resource Management templates.

There are two configuration methods in IaC: **push** and **pull**. 

In the **pull method**, the machines configured will pull the configuration from a controlling server, such as a master server. 

In the **push method**, the controlling or master server will push the configuration to the target machines. Some organizations may benefit from Infrastructure as Code frameworks such as Windows PowerShell Desired-State Configuration (DSC).

![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/208083ac194e51928826440c5c4ade48/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M2L2T3_eTdyDN9.png)

## **Configuration as Code**
The configuration of servers, code, and other resources is defined in a text file (script or definition) that is checked into version control and used as the base source for creating or updating those configurations. For instance, adding a new port to a firewall should be done by editing a text file and running the release pipeline, not by remoting into the environment and spinning up one manually.

Configuration as code scripts and environment definitions, when used with tools for managing system configuration, are usually idempotent, or can be run multiple times because the scripts or definitions will look for the state of services and install and configure if not running.

Idempotence is the property that a deployment command always sets the target environment into the same configuration, regardless of the environment’s starting state. Idempotency is achieved by either automatically configuring an existing target or by discarding the existing target and re-creating a fresh environment.

![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/40085c4b20c5c53bceaf2bfacccff77c/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M2L2T5_nQBQ9lL.png)

## **Infrastructure as a Service** 
Provides the computing infrastructure, physical or (quite often) virtual machines and other resources like virtual-machine disk image library, block and file-based storage, firewalls, load balancers, IP addresses, virtual local area networks etc.
* Amazon EC2
* Windows Azure
* Rackspace
* Google Compute Engine


## **Platform as a Service** 
Provides computing platforms which typically includes operating system, programming language execution environment, database, web server etc.
* AWS Elastic Beanstalk
* Windows Azure
* Heroku
* Force.com
* Google App Engine
* Apache Stratos

## **Software as a Service** 
Provides access to application software often referred to as "on-demand software". You don't have to worry about the installation, setup and running of the application. Service provider will do that for you. You just have to pay and use it through some client.
*  Google Apps
*  Microsoft Office 365

![](https://blogs.bmc.com/wp-content/uploads/2017/09/saas-vs-paas-vs-iaas-1024x953.png)
# Tutorials
 * [EdX’s DevOps Practices and Principles](https://www.edx.org/course/devops-practices-and-principles-3)
 * [Introduction to DevOps: Transforming and Improving Operations](https://www.edx.org/course/introduction-to-devops-transforming-and-improving-operations)
* [DevOps: The Big Picture](https://app.pluralsight.com/library/courses/devops-big-picture) 
* [Implementing DevOps in the Real World](https://app.pluralsight.com/library/courses/implementing-devops-real-world)

# DevOps Philosophy & Practice
---

**DevOps** is the combination of **cultural philosophies**, **practices**, and **tools** that increases an organization’s ability to deliver applications and services at high velocity: evolving and improving products at a faster pace than organizations using traditional software development and infrastructure management processes.

---
## CALMS
* Culture
* Automation
* Lean
* Metrics
* Sharing

![](https://res.infoq.com/articles/devops-toolchain/en/resources/7Fig1.png)

## Why DevOps?
High performing IT teams are more agile and more reliable.
They deploy code 30 times more frequently with 60 times fewer failures and if they do fail they recover 168 times faster.

The goals of DevOps span the entire delivery pipeline. They include:

* Improved deployment frequency;
* Faster time to market;
* Lower failure rate of new releases;
* Shortened lead time between fixes;
* Faster mean time to recovery (in the event of a new release crashing or otherwise disabling the current system).

## Fast Delivery Cycles
 
The goal is to create faster and faster release cycles with less and less change, to ensure that what goes into production has limited impact and we can test very specifically. Consequently, we can get things into production quickly, get feedback rapidly, and learn from our customers at a much faster cadence.
![Fast Delivery Cycles](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/a53e885ea23b008e74f7e7786a98ad7b/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M1L2T7_kWwS4Qb.png)

## DevOps Lifecycle
Traditional IT operations teams struggle with a fast release cadence because their practices make the release and operations processes reliable, but not agile. Additionally, the disconnect between development and operations increases the likelihood of mistakes and lead time when issues occur.

![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/8b5f8f3f7f658ff30d0510841823b819/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/DevOps200.1Mod1_DevOpsFundamentals_image2.png)

## DevOps Practices and Habits
### Practices
![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/cd428a6daec68dadd0f760a907002f9f/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M1L3T2_WKJNrFj.png)

### Habits
![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/f4c4685138188b8731eb5babc1f2904f/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M1L3T2_z33YOQ4.png)

## DevOps Terminology
**Agile**

>Precursor to Devops; a software development and business methodology emphasizing short, iterative planning and development cycles to provide better control and predictability and support changing requirements as projects evolve.

**DevOps**

>Software development phrase used to describe a type of agile relationship between Development and IT Operations. The goal of DevOps is to improve communication, collaboration, and processes between the various roles in the software development cycle, in order to improve and speed up software delivery.

**Continuous Delivery (CD)**
>Set of processes and practices that aims to remove waste from software production process, enables faster delivery of high-quality functionality and sets up a rapid and effective feedback loops.

**Continuous Integration (CI)**
>Development practice that requires developers to integrate code into a shared repository several times a day. Each check-in is then verified by an automated build, allowing teams to detect problems early.

**Microservices**
>Software architecture design pattern, in which complex applications are composed of small, independent processes communicating with each other using language-agnostic APIs. These services are small, highly decoupled and focus on doing a small task. 

**Release Orchestration**
>The use of tools like XL Release which manage software releases from the development stage to the actual software release itself. 

**Provisioning**
>The process of preparing new systems for users (in a Continuous Delivery scenario, typically development or test teams). The systems are generally virtualized and instantiated on demand. Configuration of the machines to install operating systems, middleware etc. is handled by automated system configuration management tools, which also verify that the desired configuration is maintained.

**Configuration Management**
>A term for establishing and maintaining consistent settings and functional attributes for a system. It includes tools for system administration tasks such as IT infrastructure automation.

**Deployment Management**
>Aims to plan, schedule and control the movement of releases to test and live environments.

**Test-Driven Development (TDD)**
>A development practice in which small tests to verify the behavior of a piece of code are written before the code itself. The tests initially fail, and the aim of the developer(s) is then to add code to make them succeed.

**Build Automation**
>Tools or frameworks that allow source code to be automatically compiled into releasable binaries. Usually includes code-level unit testing to ensure individual pieces of code behave as expected.

**Unit Testing**
>Code-level (i.e., does not require a fully installed end-to-end system to run) testing to verify the behavior of individual pieces of code. Test-driven deployment makes extensive use of unit tests to describe and verify intended behavior.

**Application Release Automation (ARA)**
>Tools, scripts or products that automatically install and correctly configure a given version of an application in a target environment, ready for use.

**Canary Release**
>A go-live strategy in which a new application version is released to a small subset of production servers and heavily monitored to determine whether it behaves as expected. If everything seems stable, the new version is rolled out to the entire production environment.


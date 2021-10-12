---

A Release Pipeline is a process that dictates how you deliver software to your end users. In practice, a release pipeline is an implementation of that pattern. The pipeline begins with code in version control and ends with code deployed to production. In between, a lot can happen. Code is compiled, environments are configured, many types of tests are run, and finally, the code is considered done.

---
## Conceptualizing a Release Pipeline
![](https://prod-edxapp.edx-cdn.org/assets/courseware/v1/f7447ee2c0a5ed89b5ace47c708b6471/asset-v1:Microsoft+DEVOPS200.1x+3T2019+type@asset+block/M3L3T4_KI0uFyw.png)

For some organizations, a release pipeline strategy and structure needs to cover services, database, web, and mobile application components, and includes:

* Binary package consumption
* Continuous integration builds
* Package publishing
* Automated testing
* Continuous delivery

## Binary package consumption
Package management allows you to reuse trusted components. An example is NuGet feeds. If you consume and reuse packages consistently, then you can keep your application fresh as those packages are updated. This is particularly important for security and compliance as the packages can be scanned, uniquely identified, and, in the event of new vulnerabilities, automatically updated.

Packages should not usually be included in version control because they may significantly increase the size of version control repositories. Better to have the packages stored in package management, such as internal NuGet feeds.

## Continuous Integration Builds
 
**Continuous Integration Builds** are builds that are triggered upon every check-in of code. They should be quick to complete and include automated tests (such as unit tests). They may or may not drop artifacts upon completion.

**Automated Builds** are valuable because they:

* Validate that code compilation doesn't just succeed “on my machine.”

* Run as many tasks as needed, such as scripting, testing, packaging, or anything else required.

* Publish to a drop folder or network share to be picked up for deployment.

* Maintain an audit history for build details, drop details, and associated work items.

In DevOps, automated builds are an integral part of continuous integration (CI), which is the practice of merging all developer working copies to a shared code line several times a day, and validating each integration with an automated build. In practice, CI is often defined as having a build with unit tests that executes at every commit or check-in to version control.

## Package publishing
Package publishing may tie into binary package consumption. You should use a version that matches the build and deployment number for full transparency (if a deployment breaks, you should be able to find the matching package quickly). The package should be hosted somewhere accessible by projects, such as NuGet feeds.

## Automated testing
Testing could include unit, integration, automated UI, web performance, and load tests. Tests should be able to run independently and as often as possible without breaking, such as in continuous integration builds or automated deployments.

## Continuous Delivery/Automated Deployment
Continuous Delivery means that deployments are triggered automatically after a build completes. The process should include picking up a compiled package of code, setting the target environment in the desired configuration state, and deploying automatically to environments. It may include approvals into QA or production environments.

Continuous delivery:

* Encourages Infrastructure as Code and configuration as code.
* Enables automated testing throughout the pipeline.
* Provides visibility and fast feedback cycles.
* Makes going to production a low-stress activity.

---

**_Deployment_** is generally defined as a continuous delivery pipeline with no manual gates between initial code check-in and production.


---
**Automated Deployments** enable predictability and efficiency when deploying releases to any environment. By implementing automated deployments, you can deploy to multiple environments either in parallel or one at a time. You set manual approvals to certain environments, redeploy to environments, and perform configuration transforms between environments (we’ll use the term “release pipeline” to indicate deployment from development through production environments). Automated deployments in DevOps are necessary for continuous delivery.
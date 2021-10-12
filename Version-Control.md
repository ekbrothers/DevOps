## Quicklinks
* [Getting Started with Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

---

**Version control** is a system that records changes to a file or set of files over time so that you can recall specific versions later. For the examples in this book, you will use software source code as the files being version controlled, though in reality you can do this with nearly any type of file on a computer.

---

Most organizations use some form of version control to manage their source code. However, not all organizations use version control effectively. 

Two version-control strategies that are sometimes overlooked are:

* Setting up an appropriate branching strategy
* Enabling transparency by linking work items to code.

One approach is to have a single branch (such as the master or main branch) that gets built in an automated continuous integration build, then deploys to a development environment upon every commit or check-in that occurs to the branch. This way, it is easier to know which changes have been released into the development environment, and eventually, into production.

The changes automatically deployed into the development environment will then get promoted or copied to the test or staging environment, and then into production. The same compiled code will get deployed to production so that there is never a situation in which unchecked code gets promoted to production. Before deploying to any environment, it is important to ensure that the changes made align to the business strategy.

## Connecting Work to Code
An easy way to verify that deployed code has value and is related to work on the backlog (rather than code that does not tie back to any work items) is by linking work items to code changes so that metadata is kept with the changes, and then with build and deployment. By connecting work in progress to code, you can validate feedback from users and the changes that were made in the code.

Some organizations use different branching strategies depending on the type of application being deployed, the degree of coupling, the organizational structure, and the deployment cadence. 

---

A general rule is to promote the **simplest branching strategy** possible to keep maintenance low and sustainability high. If you have long-lived branches that are infrequently merged, you accumulate a subtle form of technical debt.

---

In DevOps organizations, infrastructure is treated in the same way that software code is treated. **Infrastructure as Code** (IaC) is the management and provisioning of machines through code. This code is versioned in public or private repositories and shared across individuals and teams to enable more collaboration while keeping a track on changes using version control systems like Git.


## Git

---

Git is a content management and tracking system developed by Linus Torvalds, creator of Linux. It includes a directory that continuously changes as codes are added throughout application or website development. Git also tracks revisions that are performed on stored data.

---

# Quick Links
* [Github](www.github.com)
* [Getting Started in Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)
* [Git Terminology](https://git-scm.com/docs/gitglossary)
* [Git Rebasing](https://git-scm.com/book/en/v2/Git-Branching-Rebasing)
* [Hubspot Github Tutorial](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)
* [Continuous Delivery and DevOps with Azure DevOps: Source Control with Git](https://app.pluralsight.com/course-player?clipId=7c1a3899-f56b-4358-a13d-f210b8685ba2)
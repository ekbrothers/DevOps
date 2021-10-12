
---

The prospect of more automation and fewer manual security checks is an understandable concern. An article in Wired magazine offers this view: “Ultimately, DevOps will turn the IT business model on its head with shorter cycle times, automation, and deep cross-functional integration to deliver the next great idea.”

---

By bringing processes such as configuration management and automated testing into focus earlier in the deployment pipeline, fast and predictable releases are possible. Security can be introduced earlier in the process as well.

DevOps can improve security in the following ways:

* Component packages can be automatically scanned from a trusted registry.
* By using automation and operational tools, security can be addressed when development begins with code analysis, rather than as an afterthought. After fixing the code, the code that enters production is certain to have already undergone security scans and remediation. Failures can break the build.
* If a vulnerability is discovered, an automated pipeline can immediately remediate by deploying a new component package.
Using the public cloud creates a dynamic infrastructure. Unlike a static datacenter architecture, in the cloud there is no place for persistent threats to hide.
* Another option is to automate simulated attacks and stress on the system before a product or app goes to production to validate the code’s responses. If these attacks are added into the build pipeline (such as calling a script and exiting if failed), these tasks can automatically fail the build. This ensures that the release won’t get deployed to the next environment.
* Once in the production environment, automating tests for security and continuously monitoring will ensure that the application is secure.

It’s important to note, however, that security specialists are still required for monitoring and for adding security in development to DevOps. There are never any guarantees, but by automating more processes and establishing predictable pipelines and processes, good security practices can be even more consistent.
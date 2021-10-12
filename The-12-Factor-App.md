# The Twelve Factor App
* [The Twelve Factor App Website](https://12factor.net/)
---
The **Twelve-Factor App** is a methodology for building software-as-a-service apps that:

* Use declarative formats for setup automation, to minimize time and cost for new developers joining the project;
* Have a clean contract with the underlying operating system, offering maximum portability between execution environments;
* Are suitable for deployment on modern cloud platforms, obviating the need for servers and systems administration;
* Minimize divergence between development and production, enabling continuous deployment for maximum agility;
* And can scale up without significant changes to tooling, architecture, or development practices.

---




| Factor            | Description          
| -------------     |:-------------|
| [**Codebase**](https://12factor.net/codebase)        |One codebase tracked in revision control, many deploys |
| [**Dependencies**](https://12factor.net/dependencies)          |Explicitly declare and isolate dependencies      |
| [**Config**](https://12factor.net/config)     | Store config in the environment|
| [**Backing services**](https://12factor.net/backing-services)         | Treat backing services as attached resources |
| [**Build, release, run**](https://12factor.net/build-release-run)          | Treat backing services as attached resources      |
| [**Processes**](https://12factor.net/processes)    | Execute the app as one or more stateless processes      |
| [**Port binding**](https://12factor.net/port-binding)    | Export services via port binding      |
| [**Concurrency**](https://12factor.net/concurrency)  | Scale out via the process model      |
| [**Disposability**](https://12factor.net/disposability)    | Maximize robustness with fast startup and graceful shutdown      |
| [**Dev/prod parity**](https://12factor.net/dev-prod-parity)    | Keep development, staging, and production as similar as possible      |
| [**Logs**](https://12factor.net/logs)   | Treat logs as event streams      |
| [**Admin processes**](https://12factor.net/admin-processes)   | Run admin/management tasks as one-off processes      |
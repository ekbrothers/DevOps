## Why Deployment Strategies?

* reduced time to market
* client gets product value in less time
* faster feedback loops from client to production team, meaning teams can iterate on features and fix problems more readily
* improved developer morale

## Deployment Strategies

<br></br>
### "Big Bang" Deployment
"Big Bang" deployments update whole or large parts of an application in one fell swoop. This strategy goes back to the days when software was released on physical media and installed by the customer.

Big bang deployments required the business to conduct extensive development and testing before release, often associated with the "waterfall model" of large sequential releases.

Modern applications have the advantage of updating regularly and automatically on either the client side or the server side. That makes the big bang approach slower and less agile for modern teams.

Characteristics of big bang deployment include:
* All major pieces packaged in one deployment;
* Largely or completely replacing an existing software version with a new one
* Deployment usually resulting in long development and testing cycles;
* Assuming a minimal chance of failure as rollbacks may be impossible or impractical;
* Completion times are usually long and can take multiple teams’ efforts;
* Requiring action from clients to update the client-side installation.

Big bang deployments aren’t suitable for modern applications because the risks are unacceptable for public-facing or business-critical applications where outages mean huge financial loss. Rollbacks are often costly, time-consuming, or even impossible.

<br></br>
### Rolling Deployment

Rolling, phased, or step deployments are better than big bang deployments because they minimize many of the associated risks, including user-facing downtime without easy rollbacks.

In a rolling deployment, an application’s new version gradually replaces the old one. The actual deployment happens over a period of time. During that time, new and old versions will coexist without affecting functionality or user experience. This process makes it easier to roll back any new component incompatible with the old components.

Rolling deployment pattern: the old version is shown in blue and the new version is shown in green across each server in the cluster.
![](https://res.cloudinary.com/practicaldev/image/fetch/s--RbA0NHA6--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/divuxihkun2p186c9mye.png)

<br></br>
### Blue-Green, Red-Black or A/B Deployment

In this method, two identical production environments work in parallel.

One is the currently-running production environment receiving all user traffic (depicted as Blue). The other is a clone of it, but idle (Green). Both use the same database back-end and app configuration:

![](https://res.cloudinary.com/practicaldev/image/fetch/s--fJ4tYKdy--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/78dk41w8qmuy9f9pvrf6.png)

The new version of the application is deployed in the green environment and tested for functionality and performance. Once the testing results are successful, application traffic is routed from blue to green. Green then becomes the new production.

![](https://res.cloudinary.com/practicaldev/image/fetch/s--ca9C-wVZ--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/m664yyotixnqncprryf0.png)

If there is an issue after green becomes live, traffic can be routed back to blue.

In a blue-green deployment, both systems use the same persistence layer or database back end. It’s essential to keep the application data in sync, but a mirrored database can help achieve that.

You can use the primary database by blue for write operations and use the secondary by green for read operations. During switchover from blue to green, the database is failed over from primary to secondary. If green also needs to write data during testing, the databases can be in bidirectional replication.

Once green becomes live, you can shut down or recycle the old blue instances. You might deploy a newer version on those instances and make them the new green for the next release.

Blue-green deployments rely on traffic routing. This can be done by updating DNS CNAMES for hosts. However, long TTL values can delay these changes. Alternatively, you can change the load balancer settings so the changes take effect immediately. Features like connection draining in ELB can be used to serve in-flight connections.

<br></br>
### Canary Deployment
Canary deployment is like blue-green, except it’s more risk-averse. Instead of switching from blue to green in one step, you use a phased approach.

With canary deployment, you deploy a new application code in a small part of the production infrastructure. Once the application is signed off for release, only a few users are routed to it. This minimizes any impact.

With no errors reported, the new version can gradually roll out to the rest of the infrastructure. The image below demonstrates canary deployment:

![](https://res.cloudinary.com/practicaldev/image/fetch/s--7PmOiuG9--/c_limit%2Cf_auto%2Cfl_progressive%2Cq_auto%2Cw_880/https://thepracticaldev.s3.amazonaws.com/i/zvf9rbd1x38umph98zro.png)

The main challenge of canary deployment is to devise a way to route some users to the new application. Also, some applications may always need the same group of users for testing, while others may require a different group every time.

Consider a way to route new users by exploring several techniques:

Exposing internal users to the canary deployment before allowing external user access;

Basing routing on the source IP range;

Releasing the application in specific geographic regions;

Using an application logic to unlock new features to specific users and groups. This logic is removed when the application goes live for the rest of the users.
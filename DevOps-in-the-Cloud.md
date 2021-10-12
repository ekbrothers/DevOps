When you deploy to different environments in a DevOps culture, one of the first questions that should be addressed is: To what type of environment are we deploying our code? The answer depends on the type of application and the current deployment process. There are many options for cloud providers, whether public or private (such as for government), and on-premises is still a common scenario. There are advantages and disadvantages to each option, and some actions are easier to accomplish on one type and harder on another.

## Easy in the cloud, difficult on-premises:
**Scale.** Scale vertically or horizontally to as many machines as you need, only limited by the amount you wish to pay for machines. This is not always possible on-premises, where an organization might be limited by physical memory available for VMs, or have to go through a difficult process to acquire new machines.

**Data storage.** Although it varies among cloud providers, the price for storage accounts in the cloud might be less expensive than hosting your own SAN with enough space.

**Reliability.** Many cloud providers offer a service-level agreement of nearly 100% (potentially 99.9%), and that performance isn’t necessarily a guarantee on-premises.

**Time and people needed.** When on-premises, you might not carefully consider the cost for time and people involved with setting up and maintaining servers. It might take a few days to get a machine provisioned on-premises; in the cloud, it may take only minutes. Instead of assigning roles to start up and maintain machines on-premises, time can instead be used to improve cloud infrastructure or to innovate to make the DevOps process better.

**Security.** Cloud providers such as Microsoft, although they are larger targets for attacks, are constantly looking for breaches in security with aggressive white hat hackers. That might mean that a cloud is possibly more secure than your on-premises machines.

**Cost.** Cost can be optimized for variable loads. This, of course, depends on your application architecture and requirements. The cloud makes it very economic to scale out, not necessarily to scale up.

## Easy on-premises, difficult in the cloud
**Rework.** If major rework is required to get the application into the cloud, it may be too challenging to justify the time and resources needed.

**Culture.** Although rarely considered, the culture of an organization greatly affects the move to the cloud. If a rigid organizational culture favors on-premises machines, it might be challenging to move to the cloud.
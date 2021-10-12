---

Tags enable you to logically organize your resources. Only resources created through Microsoft Azure Resource Manager support tags. You cannot apply tags to classic resources.

---

[Use Tags to Organize your Azure Resources](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-using-tags)

![](https://cms.prod.oxa.microsoft.com/assets/courseware/v1/daa3b0bac1a9a0b9e2ccf1bc4a5b9728/asset-v1:Microsoft+DevOps200.1+2017_T2+type@asset+block/tags.png)
Resource Manager enables you to logically organize resources by applying tags. The tags consist of key/value pairs that identify resources with properties that you define. Examples of key/value pairs include:

dept: Accounting

environment: test

When you view resources with a particular tag, you see resources from all your resource groups. You are not limited to only the resources that are in the same resource group. This enables you to organize your resources in a way that is independent of the deployment relationships. Tags can be particularly helpful when you need to organize resources for billing or management.

Each resource or resource group can have a maximum of 15 tags. The tag name is limited to 512 characters, and the tag value is limited to 256 characters. To mark resources as belonging to the same category, apply the same tag to those resources.
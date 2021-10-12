---

## Important Links 
* [Terraform Config Language](https://www.terraform.io/docs/configuration/index.html)
* [Configuration Syntax](https://www.terraform.io/docs/configuration/syntax.html)
* [Terraform Use Cases](https://www.terraform.io/intro/use-cases.html)
* [Terraform with Azure](https://www.terraform.io/docs/providers/azurerm/index.html)
* [Terraform Arguments supported by Azure](https://www.terraform.io/docs/providers/azurerm/index.html#argument-reference)
* [Local Deployment of Terraform](https://github.com/ekbrothers/DevOps/wiki/Terraform#local-use-of-terraform)
* [Hashicorp Module Registry](https://registry.terraform.io/)


---

---
**Terraform** is a tool for building, changing, and versioning infrastructure safely and efficiently. Terraform can manage existing and popular service providers as well as custom in-house solutions.

**Configuration files** describe to Terraform the components needed to run a single application or your entire datacenter. Terraform generates an execution plan describing what it will do to reach the desired state, and then executes it to build the described infrastructure. As the configuration changes, Terraform is able to determine what changed and create incremental execution plans which can be applied.

---

## Key Features of Terraform

### Infrastructure as Code
Infrastructure is described using a high-level configuration syntax. This allows a blueprint of your datacenter to be versioned and treated as you would any other code. Additionally, infrastructure can be shared and re-used.

If this configuration changes, Terraform is able to verify what changed and it creates incremental execution plans that can be applied.

Terraform builds a graph of your resources, and parallelizes the creation and modification of any non-dependent resources. It supports custom in-house infrastructures and popular cloud providers such as Microsoft Azure. Terraform can manage Azure low-level components such as Storage and Compute, and also high-level components such as Security Groups or Resource Groups.

### Execution Plans
Terraform has a "planning" step where it generates an execution plan. The execution plan shows what Terraform will do when you call apply. This lets you avoid any surprises when Terraform manipulates infrastructure.

### Resource Graph
Terraform builds a graph of all your resources, and parallelizes the creation and modification of any non-dependent resources. Because of this, Terraform builds infrastructure as efficiently as possible, and operators get insight into dependencies in their infrastructure.

### Change Automation
Complex changesets can be applied to your infrastructure with minimal human interaction. With the previously mentioned execution plan and resource graph, you know exactly what Terraform will change and in what order, avoiding many possible human errors.

---

## Terraform CLI Commands

* [**Command List**](https://www.terraform.io/docs/commands/index.html)
    * [Plan](https://www.terraform.io/docs/commands/plan.html)
    * [Apply](https://www.terraform.io/docs/commands/apply.html)
    * [Destroy](https://www.terraform.io/docs/commands/destroy.html)


![](https://coralogix.com/wp-content/uploads/2018/07/Screen-Shot-2018-07-26-at-18.53.34.png)

## Understanding Terraform Elements

* [Resources](https://www.terraform.io/docs/configuration/resources.html)
* [Providers](https://www.terraform.io/docs/configuration/providers.html)
* [Input Variables](https://www.terraform.io/docs/configuration/variables.html)
* [Output Values](https://www.terraform.io/docs/configuration/outputs.html)
* [Local Values](https://www.terraform.io/docs/configuration/locals.html)
* [Modules](https://www.terraform.io/docs/configuration/modules.html)
* [Data Sources](https://www.terraform.io/docs/configuration/data-sources.html)
* [Configuration Syntax](https://www.terraform.io/docs/configuration/syntax.html)
* [Expressions](https://www.terraform.io/docs/configuration/expressions.html)
* [Functions](https://www.terraform.io/docs/configuration/functions.html)
* [Terraform Settings](https://www.terraform.io/docs/configuration/terraform.html)
* [Override Files](https://www.terraform.io/docs/configuration/override.html)
* [Style Conventions](https://www.terraform.io/docs/configuration/style.html)
* [Type Constraints](https://www.terraform.io/docs/configuration/types.html)


## Main Terraform Files
**variables.tf**
* Variables for access and secret keys
* variables for subnets<br>
---
**resources.tf**
* Provider
    * Defines provider
* Data
    * Pull in availability zones<br>
---
**Variable Definitions Files (.tfvars)**<br>
To set lots of variables, it is more convenient to specify their values in a variable definitions file (with a filename ending in either .tfvars or .tfvars.json) and then specify that file on the command line with `-var-file`.

Terraform also automatically loads a number of variable definitions files if they are present:
* Files named exactly terraform.tfvars or terraform.tfvars.json.
* Any files with names ending in .auto.tfvars or .auto.tfvars.json.





Let's take the example of creating an Azure Resource Group. To do that, you should start by creating a new Terraform template (main.tf):

`resource "azurerm_resource_group" "my-terraform-group" {`
    <br>`name = "my-resource-group-name"`
   <br> `location = "West US"`
<br>`}`


This should be followed by initializing a working directory containing Terraform configuration files.

`terraform init`


Preview the resources to be created by the Terraform template with:

`terraform plan`


Finally, provision the Azure resources with:

`terraform apply`


After applying this latest change to your Azure infrastructure, the actual state of the new infrastructure is stored in a **terraform.tfstate** file that was created after the first run of Terraform. By default, Terraform stores the state locally in a file named **terraform.tfstate**.

The fact that this file is stored locally makes collaboration on a shared infrastructure complex, given the merge conflicts that could result. To let a team collaborate on a shared infrastructure, one state should be used, and that is why Terraform allows the remote state feature. This is done by configuring Terraform to use Azure as a back end and Azure Blob Storage as a storage tool.

## Config Syntax
## Arguments and Values
An _argument_ assigns a value to a particular name:

`image_id = "abc123"`

`image_id` is the _argument name_<br>
`"abc123"` is the argument's value

## Blocks
A block is a container for other content

`resource "aws_instance" "example" {`
  `ami = "abc123"`

  `network_interface {`
    `# ...`
  `}`
`}`

A block has a `type` (**`resource`** in this example). Each block type defines how many labels must follow the type keyword. The `**resource**` block type expects two labels, which are aws_instance and example in the example above. A particular block type may have any number of required labels, or it may require none as with the nested network_interface block type.

After the block type keyword and any labels, the block body is delimited by the `{` and `}` characters. Within the block body, further arguments and blocks may be nested, creating a hierarchy of blocks and their associated arguments.

The Terraform language uses a limited number of top-level block types, which are blocks that can appear outside of any other block in a configuration file. Most of Terraform's features (including resources, input variables, output values, data sources, etc.) are implemented as top-level blocks.

## Identifiers
_Argument names_, _block type names_, and the names of most Terraform-specific constructs like resources, input variables, etc. are all **identifiers**.

Identifiers can contain letters, digits, underscores (`_`), and hyphens (`-`). The first character of an identifier must not be a digit, to avoid ambiguity with literal numbers.

For complete identifier rules, Terraform implements the Unicode identifier syntax, extended to include the ASCII hyphen character `-`.

[Terraform Infrastructure Design Patterns](https://opencredo.com/blogs/terraform-infrastructure-design-patterns/)

## References to Named Values
Terraform makes several kinds of named values available. Each of these names is an expression that references the associated value; you can use them as standalone expressions, or combine them with other expressions to compute new values.

The following named values are available:

`<RESOURCE TYPE>.<NAME>` is an object representing a managed resource of the given type and name. The attributes of the resource can be accessed using dot or square bracket notation.

Any named value that does not match another pattern listed below will be interpreted by Terraform as a reference to a managed resource.

If the resource has the count argument set, the value of this expression is a list of objects representing its instances.

`var.<NAME>` is the value of the input variable of the given name.

`local.<NAME>` is the value of the local value of the given name.

`module.<MODULE NAME>.<OUTPUT NAME>` is the value of the specified output value from a child module called by the current module.

`data.<DATA TYPE>.<NAME>` is an object representing a data resource of the given data source type and name. If the resource has the count argument set, the value is a list of objects representing its instances.

`path.module` is the filesystem path of the module where the expression is placed.

`path.root` is the filesystem path of the root module of the configuration.

`path.cwd` is the filesystem path of the current working directory. In normal use of Terraform this is the same as path.root, but some advanced uses of Terraform run it from a directory other than the root module directory, causing these paths to be different.

`terraform.workspace` is the name of the currently selected workspace.

Although many of these names use dot-separated paths that resemble attribute notation for elements of object values, they are not implemented as real objects. This means you must use them exactly as written: you cannot use square-bracket notation to replace the dot-separated paths, and you cannot iterate over the "parent object" of a named entity (for example, you cannot use aws_instance in a for expression).


## Using Modules
Selecting a particular module will display usage details including a code snippet you can copy and paste into your Terraform configuration to provision the specified infrastructure.

`module "consul" {`
        `source = "hashicorp/consul/aws"`
`}`

Once you have found a module you want to use, you can copy the code in the Provision Instructions into your configuration to import it. If the module has any required variables, you will need to add those to the pasted code block. When viewing the module in the registry, you can view the list of required variables in the Inputs section. You can then complete the import process by running `terraform init`.


## Local Use of Terraform
### Install Terraform Locally
1. Go to [https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html).
2. Download the applicable package to your local system.
3. Extract the package to the folder `C:\Program Files (x86)`.
This path is used as an example. However, you can also the Terraform executable to any other location in your local system.
4. Update the path environment variable to include the folder where your Terraform executable is located.
    * Go to the **Control Panel**.
    * Click **System**.
    * On a Windows 10 system, click **Advanced system settings**. This option might vary in different versions of Windows.
    * The Advanced tab of the System Properties window is displayed.
    * Click **Environment Variables** near the bottom of the window.
    * The **Environment Variables** window is displayed.
    * In the System variables pane, click **Path** and then click **Edit**.
    * Click **New**. Add the path to the folder where your Terraform executable is located.
    * Click **OK** to save your changes and then click **OK** to exit the Environment Variables windows. Then click **OK** again to exit the System Properties window.
* To verify your installation and check the version, launch Windows PowerShell and enter: `terraform -version`.
You’ll see the Terraform version displayed in the output. For example: `Terraform v0.11.8`

## Logging Into Externally Visible Services
Run <br>
<br>
`jx console`<br> 
and click on the link to log in to your Jenkins instance. 

Click on Administration and upgrade Jenkins, as well as all its plugins (Plugin Manager > scroll to the bottom and select all). 

If you fail to perform this step, you won’t be able to navigate from your GitHub pull request to your Jenkins X CI process for it.

---

## Adding Important Plugins
* Gradle Plugin
    * Install in Manage Jenkins>Plugins    
    * Activate in Manage Jenkins>Global Tool Config 

## Increasing the Number of Executors
* Under Manage Jenkins>Manage Nodes, increase number of executors

---

## Testing Jenkins-X Create
Create a bare-bones Spring Boot app from Cloud Shell: <br>
<br>`jx create spring -d web -d actuator`

Select all the defaults for the git user name, initializing git, and the commit message. You can select an organization to use if you don’t want to use your personal account. Run the following command to watch the CI/CD pipeline of your app.
<br>
`jx get activity -f <PROJECT-NAME> -w`

## Import a Pre-Existing Git Repo
1. Clone the repository <br>
`git clone <GITHUB-URL>`

2. Cd into Repository Folder
cd <REPOSITORY-FOLDER)

3. ./gradlew build

---

# Using Terraform with Jenkins X

Create a Dev, Staging and Production cluster. (The command generates three different clusters for each environment respectively in GCP. Other providers supported are aks, eks.)

```
jx create terraform -c dev=gke -c stage=gke -c prod=gke
```

# Getting GKE Credentials
Jenkins X creates a Service Account (SA) for each cluster.

For our dev cluster, it has created the jx-questerring-dev@ci-demo-206601.iam.gserviceaccount.com account.

We need to download the `json` file in order to pass as credentials to our `terraform.tf` file which contains the definition to access the Terraform Backend.

## Downloading the Credentials JSON File
To download the SA account credentials, go to the GCP Console > IAM & Admin > Service Accounts.

We find the one for our cluster which is named in our case as follows: jx-questerring-dev@ci-demo-206601.iam.gserviceaccount.com

We click on the file name > edit, then click on create key in JSON format, download and save in our project folder structure.

We now add a reference within the terraform.tf as shown below.

```
terraform {
   required_version = ">= 0.11.0"
   backend "gcs" {
   bucket      = "ci-demo-206601-questerring-terraform-state"
   prefix      = "dev"
        credentials = "key.json"
    }
}
```

## Initiating Terraform Backend
We are now ready to initiate Terraform backend. Terraform backends are used to save the Terraform State remotely. This is great for when a team needs to collaborate on making infrastructure changes, because the Terraform State is stored in the GCP Bucket that was also created when we executed our initial command to create the cluster.

```
$ terraform init   <br>

                                                                                                            
Initializing the backend...

Successfully configured the backend "gcs"! Terraform will automatically
use this backend unless the backend configuration changes.

Initializing provider plugins...
Checking for available provider plugins on https://releases.hashicorp.com...
Downloading plugin for provider "google" (2.3.0)...

Terraform has been successfully initialized!
```

We have initiated Terraform and our Terraform State is now configured to use the GCP Buket specified in the terraform.tf file.

## Executing Terraform Plan
We now can execute a terraform plan and see what will be created. At this point, we can opt to augment the terraform code.

For example, you may have an existing network that you wish to deploy the cluster in. You may also wish to enable the an add-on, or you can specify the cluster_ipv4_cidr_block and many other things (see [https://www.terraform.io/docs/providers/google/r/container_cluster.html](https://www.terraform.io/docs/providers/google/r/container_cluster.html) for details.

```
$ terraform plan                                                                                 

Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.
----

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
+ create

Terraform will perform the following actions:

+ google_container_cluster.jx-cluster
id:                                    <computed>
additional_zones.#:                    <computed>
addons_config.#:                       <computed>
cluster_autoscaling.#:                 <computed>
cluster_ipv4_cidr:                     <computed>
description:                           "jx k8s cluster provisioned and managed via Terraform."
enable_binary_authorization:           <computed>
enable_kubernetes_alpha:               "false"
enable_legacy_abac:                    "false"
enable_tpu:                            <computed>
endpoint:                              <computed>
initial_node_count:                    "3"
instance_group_urls.#:                 <computed>
ip_allocation_policy.#:                <computed>
location:                              <computed>
logging_service:                       "logging.googleapis.com"
master_auth.#:                         <computed>
master_ipv4_cidr_block:                <computed>
master_version:                        <computed>
monitoring_service:                    "monitoring.googleapis.com"
name:                                  "questerring-dev"
network:                               "default"
network_policy.#:                      <computed>
node_config.#:                         <computed>
node_locations.#:                      <computed>
node_pool.#:                           <computed>
node_version:                          <computed>
private_cluster:                       <computed>
project:                               <computed>
region:                                <computed>
remove_default_node_pool:              "true"
resource_labels.%:                     "3"
resource_labels.created-by:            "me"
resource_labels.created-timestamp:     "20190326093418"
resource_labels.created-with:          "terraform"
zone:                                  "us-west1-a"

+ google_container_node_pool.jx-node-pool
id:                                    <computed>
autoscaling.#:                         "1"
autoscaling.0.max_node_count:          "5"
autoscaling.0.min_node_count:          "3"
cluster:                               "questerring-dev"
initial_node_count:                    <computed>
instance_group_urls.#:                 <computed>
location:                              <computed>
management.#:                          "1"
management.0.auto_repair:              "true"
management.0.auto_upgrade:             "false"
max_pods_per_node:                     <computed>
name:                                  "default-pool"
name_prefix:                           <computed>
node_config.#:                         "1"
node_config.0.disk_size_gb:            "100"
node_config.0.disk_type:               <computed>
node_config.0.guest_accelerator.#:     <computed>
node_config.0.image_type:              <computed>
node_config.0.local_ssd_count:         <computed>
node_config.0.machine_type:            "n1-standard-2"
node_config.0.metadata.%:              <computed>
node_config.0.oauth_scopes.#:          "7"
node_config.0.oauth_scopes.1277378754: "https://www.googleapis.com/auth/monitoring"
node_config.0.oauth_scopes.1693978638: "https://www.googleapis.com/auth/devstorage.full_control"
node_config.0.oauth_scopes.172152165:  "https://www.googleapis.com/auth/logging.write"
node_config.0.oauth_scopes.1733087937: "https://www.googleapis.com/auth/cloud-platform"
node_config.0.oauth_scopes.2184564866: "https://www.googleapis.com/auth/service.management"
node_config.0.oauth_scopes.299962681:  "https://www.googleapis.com/auth/compute"
node_config.0.oauth_scopes.3663490875: "https://www.googleapis.com/auth/servicecontrol"
node_config.0.preemptible:             "true"
node_config.0.service_account:         <computed>
node_count:                            "3"
project:                               <computed>
region:                                <computed>
version:                               <computed>
zone:                                  "us-west1-a"
Plan: 2 to add, 0 to change, 0 to destroy.
```

----

Note: You didn't specify an "-out" parameter to save this plan, so Terraform
can't guarantee that exactly these actions will be performed if
"terraform apply" is subsequently run.

## Create Cluster Using Terraform Apply
```
$ terraform apply
.....trimmed for brevity
Apply complete! Resources: 2 added, 0 changed, 0 destroyed.

Outputs:

cluster_endpoint = 35.203.147.59
cluster_master_version = 1.11.7-gke.12
```

## Set Kubectl Context
Let us access the cluster using kubectl. In order to do that, we need to get credentials. We execute the following command (which you can get from the UI on GCP right from the cluster connect window)

```
$ gcloud container clusters get-credentials questerring-dev --zone us-west1-a --project ci-demo-206601 
                        
Fetching cluster endpoint and auth data.
kubeconfig entry generated for questerring-dev.
```

This has effectively modified our kubeconfig file and we now have a new context.

Executing the following command, we see our new cluster (in bold)

```
$ jx context                                                                                                                      
BigDaddyO
arn:aws:eks:us-west-2:653931956080:cluster/jxcluster
gke_ci-demo-206601_europe-west1-b_sirjenkinsgke
gke_ci-demo-206601_us-west1-a_chingold
gke_ci-demo-206601_us-west1-a_questerring-dev
gke_ci-demo-206601_us-west1-a_sirjenkinsgke
gke_ci-demo-206601_us-west1-a_sirjenkinsx
gke_ci-demo-206601_us-west1_sirjenkinsxgke
minikube
1553553075211690000@jxcluster.us-west-2.eksctl.io
```


## Installing Jenkins X on Cluster
To install Jenkins X, we simply run jx install and follow the prompts.

{{ note }} NOTE that can pass additional flags as per your prefernces. For example set the default admin password like so --default-admin-password=MyPassw0rd (see other options by typing jx install --help {{ /note }}

Now that we have Jenkins X installed, we can deploy an app etc. We make sure it is up and running.

## Modify Clusters
There are certain properties that can be modified without forcing a recreation of the clusters. You do not want to recreate them as your data will be lost. Only changes that update the clusters are supported.

We are going to modify the cluster and add an add-on for the Dashboard which is typically disabled.

To do that we change the following within the cluster declaration in main.tf and add the following (in bold):

```
resource "google_container_cluster" "jx-cluster" {
    name                     = "${var.cluster_name}"
    description              = "jx k8s cluster provisioned and managed via Terraform."
    zone                     = "${var.gcp_zone}"
    enable_kubernetes_alpha  = "${var.enable_kubernetes_alpha}"
    enable_legacy_abac       = "${var.enable_legacy_abac}"
    initial_node_count       = "${var.min_node_count}"
    remove_default_node_pool = "true"
    logging_service          = "${var.logging_service}"
    monitoring_service       = "${var.monitoring_service}"

    resource_labels {
        created-by = "${var.created_by}"
        created-timestamp = "${var.created_timestamp}"
        created-with = "managed by terraform"
    }

    lifecycle {
        ignore_changes = ["node_pool"]
    }

    addons_config {
        kubernetes_dashboard {
            disabled = false
        }
    }

}
```

Then we run the terraform plan, output shows a change to the cluster as expected.

```
terraform plan 
```
                                                                                                            

Refreshing Terraform state in-memory prior to plan...
The refreshed state will be used to calculate this plan, but will not be
persisted to local or remote state storage.


```
google_container_cluster.jx-cluster: Refreshing state... (ID: sposcar-dev)
google_container_node_pool.jx-node-pool: Refreshing state... (ID: us-west1-a/sposcar-dev/default-pool)
```

----

An execution plan has been generated and is shown below.
Resource actions are indicated with the following symbols:
~ update in-place

Terraform will perform the following actions:

```
~ google_container_cluster.jx-cluster
addons_config.0.kubernetes_dashboard.0.disabled: "true" => "false"
resource_labels.created-with:                    "terraform" => "managed by terraform"

Plan: 0 to add, 1 to change, 0 to destroy.

Note: You didn't specify an "-out" parameter to save this plan, so Terraform
can't guarantee that exactly these actions will be performed if
"terraform apply" is subsequently run.
```

Accessing kubernetes dashboard
Now that our change has taken effect on our cluster, lets access the Dashboard.

{{ note }} NOTE: This dashboard is deprecated, and we are only showing you in the context of modifying your cluster to add an add-on. Please use the GKE built-in UI {{ /note }}

Get Access token
gcloud config config-helper --format=json | jq -r '.credential.access_token'
Copy the token from the output of that command.

Next, execute kubectl proxy which will enable you to access via the following URL

http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy

Paste the token and now you should be able to access the now deprecated dashboard via the browser.




















## Create an app

Now that you have a working cluster containing a JX install, we are going to create an
application, that can be built & deployed with Jenkins-X

### Using a quickstart

JX has a `create quickstart` command that will create a build from a standardised template.
To run this command, type the following:

```bash
jx create quickstart
```

For this example, lets select `golang-http` and choose a name for the new application such
as `cloudshell-tutorial`.

JX will then guide you through setting up the git repository for the application.

If this is the first application you have created, it may take a few minutes to download all
of the required builder images in order to build/deploy the application.  To view the status 
of the app, you can use the following:

```bash
jx get activity -f cloudshell-tutorial -w
```

To view the app in each environment along with urls

```bash
jx get applications
```

### Promote the app to production

Using the `jx promote` command, you can push this version from staging to
production.

```bash
cd cloudshell-tutorial
```
_If you have 2FA enabled on your GitHub account, then you may need to use an api token as your password when prompted._

```bash
jx promote cloudshell-tutorial --version 0.0.1 --env production
```

You can check the progress of the production deployment using:

```bash
jx get activity -f cloudshell-tutorial -w
```

```bash
jx get applications
```



---

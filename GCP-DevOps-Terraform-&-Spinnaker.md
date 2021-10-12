# Table of Contents
- [Helpful Links](#helpful-links)
- [Spinnaker](#spinnaker)
  * [Why Use Spinnaker?](#why-use-spinnaker-)
  * [What is Spinnaker Made Of?](#what-is-spinnaker-made-of-)
  * [Halyard Vs Helm Vs. Deployment Manager](#halyard-vs-helm-vs-deployment-manager)
    + [Halyard](#halyard)
  * [Using Spinnaker with Kubernetes](#using-spinnaker-with-kubernetes)
- [How-to: Employing Terraform in GCP](#how-to--employing-terraform-in-gcp)
* [Continuous Delivery Pipelines with Spinnaker and Google Kubernetes Engine](https://cloud.google.com/solutions/continuous-delivery-spinnaker-kubernetes-engine)
* [**Use this one** Continuous Delivery to Kubernetes Using Spinnaker](https://codelabs.developers.google.com/codelabs/cloud-spinnaker-kubernetes-cd/#0)

# Helpful Links
* [Spinnaker on GCP with GKE](https://medium.com/google-cloud/spinnaker-on-gcp-with-gke-edfa994652f7)


# Enable APIs
Navigate to the Google Cloud Console and enable the following APIs:

* [Google Identity and Access Management (IAM) API](https://console.developers.google.com/apis/api/iam.googleapis.com/overview)
* [Google Cloud Resource Manager API](https://console.developers.google.com/apis/api/cloudresourcemanager.googleapis.com/overview)

# Spinnaker
<br><br>
![](https://i.imgur.com/kBfEMNp.jpg)
## Why Use Spinnaker?
* Allows reliable deployment across multiple GCP Projects and GKE Clusters
* Works with Google Cloud’s software vulnerability scanner,
* Provides Binary Authorization that verifies the authenticity of code releases before deployment.
* Launches pipelines based on Google Cloud Build Triggers
* Allows for low-touch engineering releases

Spinnaker’s application management features allow developers to view and manage cloud resources.
Applications, Clusters, and Server Groups are the key concepts Spinnaker uses to describe services. Load balancers and Firewalls describe how services are exposed to users.

## What is Spinnaker Made Of?
Spinnaker is composed of a number of microservices:

* **[Deck](https://github.com/spinnaker/deck)** is the browser-based UI.
* **[Gate](https://github.com/spinnaker/gate)** is the API gateway. The Spinnaker UI and all API callers communicate with Spinnaker via Gate.
* **[Orca](https://github.com/spinnaker/orca)** is the orchestration engine. It handles all ad-hoc operations and pipelines.
* **[Clouddriver](https://github.com/spinnaker/clouddriver)** is responsible for all mutating calls to the cloud providers and for indexing/caching all deployed resources.
* **[Front50](https://github.com/spinnaker/front50)** is used to persist the metadata of applications, pipelines, projects and notifications.
* **[Rosco](https://github.com/spinnaker/rosco)** is the bakery. It is used to produce machine images (for example GCE images, AWS AMIs, Azure VM images). It currently wraps Packer, but will be expanded to support additional mechanisms for producing images.
* **[Igor](https://github.com/spinnaker/igor)** is used to trigger pipelines via continuous integration jobs in systems like Jenkins and Travis CI, and it allows Jenkins/Travis stages to be used in pipelines.
* **[Echo](https://github.com/spinnaker/echo)** is Spinnaker’s eventing bus. It supports sending notifications (e.g. Slack, email, Hipchat, SMS), and acts on incoming webhooks from services like GitHub.
* **[Fiat](https://github.com/spinnaker/fiat)** is Spinnaker’s authorization service. It is used to query a user’s access permissions for accounts, applications and service accounts.
* **[Kayenta](https://github.com/spinnaker/kayenta)** provides automated canary analysis for Spinnaker.
* **[Halyard](https://github.com/spinnaker/halyard)** is Spinnaker’s configuration service. Halyard manages the lifecycle of each of the above services. It only interacts with these services during Spinnaker start-up, updates, and rollbacks.
By default, Spinnaker binds ports accordingly for all the above-mentioned microservices.

## Halyard Vs Helm Vs. Deployment Manager
Halyard is a tool for configuring, installing, and updating Spinnaker.
### Halyard 
**Pros:**
* supported by the official spinnaker project
* super easy to get started
**Cons:**
* requires a bit of extra config through the hal cli

## Using Spinnaker with Kubernetes
Using Spinnaker with Kubernetes provides:
* Seamless resource mapping especially with the v2 of the k8s.
* Advance deployment strategy like canary.
* Deployment Rollback.
* Spinnaker first class support for k8s unlike tools like jenkins.
* Spinnaker will version deployed manifest to k8s to use for rollbacks.
* Spinnaker will monitor the health of your application in k8s. It allows not only to deploy to but gives a good view of the health of the k8s application and cluster.
* Integration for CI tools like jenkins to pull artifacts.


# Installing Spinnaker on 

# How-to: Employing Terraform in GCP

Have the following tools locally:

* An existing SSH Key
* Terraform

## [Check and/or Create an existing SSH Key](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)
1. Open Git Bash.

2. Enter ls -al ~/.ssh to see if existing SSH keys are present:

     * `$ ls -al ~/.ssh`<br>
     * Lists the files in your .ssh directory, if they exist

3. Check the directory listing to see if you already have a public SSH key.

    * By default, the filenames of the public keys are one of the following:

        * id_dsa.pub
        * id_ecdsa.pub
        * id_ed25519.pub
        * id_rsa.pub

* Paste the text below, substituting in your GitHub email address.

    * `$ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"`<br>
        * This creates a new ssh key, using the provided email as a label.

    * `> Generating public/private rsa key pair.`<br>

When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.

* `> Enter a file in which to save the key (/c/Users/you/.ssh/id_rsa):[Press enter]`<br>

* At the prompt, type a secure passphrase. 
    * `> Enter passphrase (empty for no passphrase): [Type a passphrase]> Enter same passphrase again: [Type passphrase again]`

## [Adding your SSH key to the ssh-agent](https://help.github.com/en/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent#adding-your-ssh-key-to-the-ssh-agent)

1. **Ensure the ssh-agent is running:**

    * If you are using the Git Shell that's installed with GitHub Desktop, the ssh-agent should be running.

    * If you are using another terminal prompt, such as Git for Windows, you can use the "Auto-launching the ssh-agent" instructions in "Working with SSH key passphrases", or start it manually:

    * start the ssh-agent in the background
    * `$ eval $(ssh-agent -s)` > Agent pid 59566

## Enable Compute Engine API in Google Cloud Platform
When an API requires an API key and the API is associated with a Google Cloud Platform (GCP) project that you don't have access to, you have the following options to obtain an API key:

* **Option 1**: Ask a member of the GCP project to create an API key for you.

* **Option 2**: Ask a member of the GCP project to grant you access to the project so that you can create an API key in the same project that the API is associated with.

* **Option 3**: Ask a member of the GCP project to grant you access to enable the API in your own GCP project so that you can create an API key.

### Enabling an API
If you used option 3 and asked someone to grant you access to enable the API, follow the steps below to enable the API in your own GCP project.

**To enable an API:**

* In the GCP Console, go to APIs & services for your project.
GO TO APIS & SERVICES
* On the **Library page**, click **Private APIs**. If you don't see the API listed, that means you haven't been granted access to enable the API.
* Click the API you want to enable. If you need help finding the API, use the search field.
* In the page that displays information about the API, click **Enable**.

## Getting Project Credentials
**Set up a service account key, which Terraform will use to create and manage resources in your GCP project.** <br>

* [Create service account key page.](https://console.cloud.google.com/apis/credentials/serviceaccountkey?_ga=2.71819153.-309632114.1570641211&_gac=1.50265172.1570712834.Cj0KCQjwrfvsBRD7ARIsAKuDvMMBa5LFZHCUT1PRgPZuoAEur94713L0RzEEzgmI8tlavT7UbvgqBuoaAvvgEALw_wcB) <br>
* Select the default service account or create a new one, select **JSON** as the key type, and click **Create**.

* This downloads a JSON file with all the credentials that will be needed for Terraform to manage the resources. This file should be located in a secure place for production projects, but for this example move the downloaded JSON file to the project directory.

## Setting up Terraform on GCP
Create a new directory for the project to live and create a main.tf file for the Terraform config. The contents of this file describe all of the GCP resources that will be used in the project.

`// Configure the Google Cloud provider`
`provider "google" {`
 `credentials = "${file("CREDENTIALS_FILE.json")}"`
 `project     = "flask-app-211918"`
 `region      = "us-west1"`
`}`

<br>**Set the project ID from the first step to the project property and point the credentials section to the file that was downloaded in the last step.** The provider “google” line indicates that you are using the Google Cloud Terraform provider and at this point you can run terraform init to download the latest version of the provider and build the .terraform directory.

`terraform init`

`Initializing provider plugins...`
`- Checking for available provider plugins on https://releases.hashicorp.com...`
`- Downloading plugin for provider "google" (1.16.2)...`

`The following providers do not have any version constraints in configuration, so the latest version was installed.`

`To prevent automatic upgrades to new major versions that may contain breaking changes, it is recommended to add version = "..." constraints to the corresponding provider blocks in configuration, with the constraint strings suggested below.`

`* provider.google: version = "~> 1.16"`

`Terraform has been successfully initialized!`
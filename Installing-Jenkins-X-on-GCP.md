
Adapted from [here](https://go.cloudbees.com/docs/cloudbees-jenkins-x-distribution/installation/gcp/) and [here](http://gmacario.github.io/2018/10/09/install-jenkinsx-on-gcp.html) and [here](https://github.com/jenkins-x/jx-tutorial/edit/master/tutorials/install-jx-on-gke/lesson.md)

## Prereqs
Installing Jenkins X on Google Cloud Platform Shell requires the following supported services installed and configured prior to installation:

* A Google Cloud Platform (GCP) account.

* A GCP project for your Jenkins X installation. It is recommended that you create a new GCP project, separate from your other development and production clusters.

* Create and/or select a project.
  
   * To create a project: `gcloud projects create <project-name>`
   * To select the project in which this tutorial will be executed: 
<br>`gcloud config set project <PROJECT_ID>`
         
  * Billing must be enabled (note there's a $300 credit, free tier for new accounts)



---

## Step 1: Installing Dependencies

1.1 Install the `jx` binary and add it to your PATH.


`curl -L https://github.com/jenkins-x/jx/releases/download/v1.3.79/jx-linux-amd64.tar.gz | tar xzv`<br>
`sudo mv jx /usr/local/bin`<br>
`export PATH=$PATH:.`<br>
<br>

JX will attempt to locate any required dependencies, if it discovers that some are missing it will prompt to install them for you in the `~/.jx/bin` folder.  It is recommended that
you allow `jx` to install any missing dependencies.


---


## Step 2. Creating a Jenkins X Cluster

### Prereqs
Have the following configured:

* A Google Cloud Platform (GCP) account for creating kubernetes clusters

* Access to the GitHub remote Git provider, which allows users to create organizations and multiple user accounts:

    * An Organization from which you invite existing users (in this example, the organization is called acmecorp). Create an organization by clicking the + button at the top right of the GitHub project page or through the Create an organization page.

    * A GitHub user account for creating and managing development repositories (for example acmeuser). Invite the user to your organization.

    * A bot user that automates pull request notifications and creates preview environments for quick validation and acceptance for code merging. The bot account must have a token created by your organization that authenticates the bot and allows it to perform various tasks on the repositories within your organization. In the examples, a GitHub account named acmebot is used.

---

2.2 Run jx create cluster at the command-line to initialize the cluster on your Google Kubernetes Engine (GKE) account with a specified name, for example acmecluster1:<br>
     ```apache
      jx create cluster gke --skip-login=true --skip-installation -n 
      <CLUSTERNAME>
     ```

## Step 3. Configure Your Cluster

JX will then provide you with defaults for the basic configuration options for your cluster. You will be prompted to make some selections, for example:

* Google Cloud Zone - select a zone that is near to you

The defaults provided include:
* A generated name for your cluster
* Cluster type `Zonal`
* Machine type - `n1-standard-2`
* Minimum number of Nodes - `3`
* Maximum number of Nodes - `5`
* Use of preemptible VMs - `No`
* Access Google Cloud Storage / Google Container Registry - `Yes`
* Enable Cloud Build, Container Registry & Container Analysis APIs - `Yes`
* Enable Kaniko for building container images - `No`

Your cluster < name > in < zone > should be created for you.

#### GitHub connectivity

If this is the first time you have run `jx` in this cloudshell, `jx` will prompt you for a github username & api token.  If you already have one, simply enter the values when prompted. 

If you don't have an api token, click on the link provided to generated one and enter the token value into the prompt.

The program asks you for a Pipeline Bot Git username (for example acmebot). This creates a bot for automating your GitOps process by promoting code from your development environment to your staging and/or production environments.
* Create a new GitHub account strictly for the build control bot
* Invite the bot account to your organization
* Create a Git token for the Pipeline Bot with the correct permissions via this GitHub Link and copy the 40 character token

> **Important**<br>
> The 40 character token generated by GitHub is only shown once so you must copy this immediately before you close the >browser tab or window, as the token cannot be retrieved once it is displayed.
> Paste the copied GitHub token created for the Pipeline Bot when prompted

* The program opens a web browser to choose the email address associated with your GCP account, then prompts you to allow the Google Cloud SDK to access your account.

* Back at the command-line, the jx create cluster program prompts you to choose your project from the available list.

* The program prompts you to choose the Zone nearest to where you would like to install your cluster. For example, if you want your cluster to serve users primarily in the east coast of the United states, you choose us-east1-b from the available list.

* The program prompts you to enter a Storage Bucket URLs for saving various storage resources:
    * Logs: You can use an existing storage bucket URL or press Enter and a bucket will be created for you.
    * Reports: You can use an existing storage bucket URL or press Enter and a bucket will be created for you.
    * Repository: You can use an existing storage bucket URL or press Enter and a bucket will be created for you.

* The program runs automatically through default questions and begins creating the cluster in your specified zone.

     `Your Kubernetes context is now set to the namespace: jx`<br>
     `To switch back to your original namespace use: jx namespace default`<br>
     `Or to use this context/namespace in just one terminal use: jx shell`<br>
     `For help on switching contexts see: https://jenkins-x.io/developing/kube-context/` <br>
     `To import existing projects into Jenkins:       jx import` <br>
     `To create a new Spring Boot microservice:       jx create spring -d web -d actuator` <br>
     `To create a new microservice from a quickstart: jx create quickstart` <br>


---

## Step 4. Jenkins Installation  

* Select Jenkins Installation Type - recommended `Static Jenkins Server and Jenkinsfiles`
* Pick workload build pack - recommend `Kubernetes Workloads: Automated CI+CD with GitOps Promotion`

Next, `jx` will attempt to configure Jenkins connectivity.  This should be done automatically, 
but sometimes Jenkins is not able to start intime.  In this instance, you will be asked to 
login to Jenkins using the admin user.  The password for the admin user will be displayed in the 
console.  At this point, follow the instructions to add the Jenkins API token.




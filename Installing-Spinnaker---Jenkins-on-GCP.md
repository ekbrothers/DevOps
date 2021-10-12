Edited from [this site](https://codelabs.developers.google.com/codelabs/bake-and-deploy-pipeline/#2).

#### 1. Run this command, then follow the prompts:<br>
`curl https://sdk.cloud.google.com | bas`h
#### 2. Authenticate gcloud to your account: <br>
`gcloud auth login <your email address`>
#### 3. Enable the Compute Engine API <br>
`gcloud services enable compute.googleapis.com --project <your project id>`

### Provisioning Spinnaker (with Jenkins)
`gcloud compute instances create spinnaker --project avian-muse-249214 --zone us-east1-b --image `spinnaker-codelab` --image-project marketplace-spinnaker-release --machine-type n1-highmem-4 --scopes cloud-platform --metadata startup-script=/var/spinnaker/startup/first_codelab_boot.sh,gce_account=my-google-account`

---

`gcloud services enable compute.googleapis.com --project strong-maker-256013`


---


`gcloud compute ssh spinnaker --project avian-muse-249214 --zone us-east1-b --ssh-flag="-L 8084:localhost:8084" --ssh-flag="-L 9000:localhost:9000" --ssh-flag="-L 5656:localhost:5656"`


## Create an application in Spinnaker
An application, in Spinnaker, represents the service you are going to deploy, configuration for that service, and the infrastructure on which it will run.

1. Navigate to the Spinnaker UI: http://localhost:9000.
2. On the Spinnaker home page, click Actions (top-right), and select Create Application.
3. Fill out these fields, in the New Application dialog:
* **Name:** "**NAME**"
* **Owner Email:** <your email address>
* Click **Create**.

## Upgrading Jenkins

`sudo service jenkins stop`<br>

### 1. On GCP Cloud SDK Shell, SSH in to the terminal.<br>
`gcloud compute instances create spinnaker --project **strong-maker-256013** --zone **us-east1-b** --image `spinnaker-codelab` --image-project marketplace-spinnaker-release --machine-type n1-highmem-4 --scopes cloud-platform --metadata startup-script=/var/spinnaker/startup/first_codelab_boot.sh,gce_account=my-google-account`

### 2. Upgrade the distribution<br>
`sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade `

### 3. cd into /usr/share/jenkins - this is where the jenkins.war file lives<br>
`cd /usr/share/jenkins`

### 4. Download newest Jenkins *.war file<br>
`sudo wget http://updates.jenkins-ci.org/download/war/2.200/jenkins.war`

### 5. Rename old jenkins file
`sudo mv jenkins.war jenkinsold.war `<br>
`sudo mv jenkins.war.1 jenkins.war`

### 6. Stop and start the jenkins service
`sudo service jenkins stop`<br>
`sudo service jenkins start`

or use systemctl

# Connecting Jenkins and Spinnaker
[https://www.spinnaker.io/setup/ci/jenkins/](https://www.spinnaker.io/setup/ci/jenkins/)

## Download and Install Plugins

### Install Strict Crumb Issuer Plugin in Jenkins:

* Under Manage Jenkins > Plugin Manager > Available, search for Strict Crumb Issuer Plugin, select Install.

![](https://www.spinnaker.io/setup/ci/strict_crumb_issuer_plugin_install.png)

#### Enable CSRF protection in Jenkins:

* Under Manage Jenkins > Configure Global Security, select Prevent Cross Site Request Forgery exploits.

* Under Crumb Algorithm, select Strict Crumb Issuer.

* Under Strict Crumb Issuer > Advanced, deselect Check the session ID

![](https://www.spinnaker.io/setup/ci/jenkins_enable_csrf_strict.png)

# Problems

### Javascript error in Jenkins
This possible error is caused by an issue with the Cloudbees distribution.  SSH into lib/var/jenkins/plugins directory, delete all of the plugins, and restart.  In order to do so, you may need to make yourself the owner of the directories.  

`sudo chown --recursive lib/var/jenkins/plugins` <br>

`sudo -rm --recursive lib/var/jenkins/plugins/*.*`


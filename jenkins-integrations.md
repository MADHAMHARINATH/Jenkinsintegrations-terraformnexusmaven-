## **Prerequisites**
* Accounts in GCP, AWS, AZURE
* Make sure sudo permissions are available


## **Setup Jenkins server in GCP.**
* Create a VM(instance-1) with Ubuntu-18.04.
* Install [Java](https://github.com/ncodeit-io/devops-cloud/blob/main/mini-project/install_java8.sh)
```
git clone https://github.com/ncodeit-io/devops-cloud.git
sudo ./devops-cloud/mini-project/install_java8.sh
```
* Install [Jenkins](https://github.com/ncodeit-io/devops-cloud/blob/main/mini-project/install_jenkins.sh).
```
git clone https://github.com/ncodeit-io/devops-cloud.git
sudo ./devops-cloud/mini-project/install_jenkins.sh
```
* Login to Jenkins dashboard.


## **Setup Nexus server in Azure.**
* Create a VM(instance-2) with Ububtu-18.04
* Install [Java](https://github.com/ncodeit-io/devops-cloud/blob/main/mini-project/install_java8.sh)
```
git clone https://github.com/ncodeit-io/devops-cloud.git
sudo ./devops-cloud/mini-project/install_java8.sh
```
* Install [Nexus](https://github.com/ncodeit-io/devops-cloud/blob/main/mini-project/nexus_installation_8081.sh)
```
git clone https://github.com/ncodeit-io/devops-cloud.git
sudo ./devops-cloud/mini-project/nexus_installation_8081.sh
```
* Then login to Nexus dashboard.

## **Now integrate Jenkins(on instance-1) with Nexus(on instance-2)**
* Install required pluggin.
* From Dashboard goto Manage jenkins -> Configure system & * add Nexus by providing necessary details.


## **Setup the freestyle job and integrate it with slack.**
* Install required plugins for slack notification
* From Dashboard goto Manage jenkins -> Configure system & * add Slack byproviding necessary details.
* Create a freestyle job.
* Add Slack Notifications from Post-build action.
* Run the job.
* Then stop the Nexus server.

## **Install Ansible on the Jenkins server(instance-1).**
* Install [Ansible](https://github.com/ncodeit-io/devops-cloud-public-repo/blob/main/install-ansible.sh)
```
git clone https://github.com/ncodeit-io/devops-cloud-public-repo/blob/main/install-ansible.sh
sudo ./devops-cloud-public-repo/install-ansible.sh
```

## **Install and setup http server on Jenkins server(instance-1)**
* Install [http](https://github.com/ncodeit-io/devops-cloud/blob/main/tomcat-apache-nginx/apache.md) on port 7777
```
git clone https://github.com/ncodeit-io/devops-cloud.git
sudo ./devops-cloud/tomcat-apache-nginx/apache.md
```
## **Setup a jenkins job that should run every 10 minutes using cron syntax.**
* Create a freestyle project.
* Select "Build periodically" from "Build Triggers" tab.
* Give the cron syntax which runs every 10minutes.

## **Setup a jenkins job that should run an ansible-playbook which restarts a http server running on the Jenkins server**
* Install required pluggins for ansible
* Create an Ansible-playbook which restarts http server
* Create a freestyle job & select "Invoke Ansible Playbook" from "Builds" tab.
* Then provide the details like path, host file etc.,.
* Then build the job which will restart the http server.
	
## **Setup a jenkins job that runs terraform template to launch an ec2 instance**
* Create terraform template to launch ec2 instance
* Create a new freestyle job and configure it
* From Build tab select Executive shell and enter the below commands
```	
cd <path-of-terraform-file>
sudo /usr/local/bin/terraform init
sudo /usr/local/bin/terraform plan
sudo /usr/local/bin/terraform apply --auto-approve
```
* Check ec2 instance in AWS

## **Use zabbix to monitor jenkins server/ec2 instance**
* Install [Zabbix]() on GCP
* Open Zabbix dashboard
* Now install [Zabbix agent](https://www.linuxtechi.com/add-linux-host-zabbix-server-for-monitoring/) in Jenkins server(instance-1)
* Also install [Zabbix agent](https://www.linuxtechi.com/add-linux-host-zabbix-server-for-monitoring/) in AWS EC2 we just launched
* Add these two machines to Zabbix dashboard for monitoring.

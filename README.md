# DevOps-Project

DevOps-Project : Web Application AWS Deployment using Ansible 
The project approach is about deploying a webapp to AWS. To make it more simple this web app been developed just by using a single HTML page served with nginx.
At the dev environment, AWS VPC and auto-scaling group setup made at the back an elastic load balancer. During deployment stage, the AMI with current application state and associated with auto-scaling configuration. Auto-scaling will deal with creating, launching or replacing existing instances one after other including new instances of an updated AMI.

## Prerequisites: 
	* Ruby  2.0
	* Python 2.7.9
	* Ansible

## Tests: Automated test performed using cucumber.

## Deployment in AWS: Below Two steps are used in deploying the current build:
	• Step 1: Generate a new AMI from the current Ansible build:
			`AWS_ACCESS_KEY=... AWS_SECRET_KEY=... ansible-playbook bake_ami.yml -e "key_name=*valid key name"`
	• Step 2: deploy the current AMI to a new autoscaling launch configuration. 
			`AWS_ACCESS_KEY=... AWS_SECRET_KEY=... ansible-playbook deploy_aws.yml -e "key_name=*valid key name"`
	
## Ansible resources:
	• “./local_dev.yml” playbook used for local dev environment.
	• “./bake_ami.yml” playbook used for creating an AWS AMI from the current application build. 
	• “./deploy_aws.yml”  playbook used for creating a launch config for the AMI described in `/vars/current_ami.yml`
	• “./roles/nginx/” role used for configuring nginx.
	• “./roles/web_app/” role used for deploying web app code.
	• “./roles/aws_core/” role used for basic AWS infrastructure setup.


	

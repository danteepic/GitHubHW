# GitHubHW
HW for GitHub


## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Elk Stack.jpg

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Filebeat.

See playbook.yml for the DVWA and ELK playbook builds. 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the Damn Vulnerable Web Application.
Load balancing ensures that the application will be highly redundant, in addition to restricting  unauthorized accessing to the network.

What aspect of security do load balancers protect? What is the advantage of a jump box? 
Connects into the vitual network from external sources and internal machines by allowing a connection to private addresses.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the container and system logs.

What does Filebeat watch for? 
Monitors the log files or locations that you specify, collects log events.

What does metricbeat record?
Monitor your servers by collecting metrics from the system and services running on the server.

| name    | function            | ip address | OS           |
|---------|---------------------|------------|--------------|
| elk     | log aggregator      | 10.1.1.2   | ubuntu 18.04 |
| dvwa1   | virtual machine     | 10.0.1.2   | ubuntu 18.04 |
| dvwa2   | virtual machine     | 10.0.1.3   | ubuntu 18.04 |
| dvwa3   | virtual machine     | 10.0.1.4   | ubuntu 18.04 |
| jumpbox | entry point gateway | 10.0.1.5   | ubuntu 18.04 |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 
Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

| name    | publicly accessible | allowed ip addresses  |
|---------|---------------------|-----------------------|
| elk     | yes via port 9200   | From DVWA machines    |
| dvwa1   | no                  | n/a                   |
| dvwa2   | no                  | n/a                   |
| dvwa3   | no                  | n/a                   |
| jumpbox | yes via ssh         | From home private IP  |


### Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because leaves no chance for mistakes and logging in faster.

The playbook implements the following tasks:
*ssh to jumpbox
*install docker.io
*pull Ansible container 
*build and run ELK playbook
*configure security rules to allow inbound ports 9200,5601

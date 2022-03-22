## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Elk-Stack/Diagrams/Azure.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

(Elk-Stack/Linux/filebeat-config.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
Load balancers protect the availability of an application. A jump box is a secure computer that all admins first connect to before launching any administrative task or use as an origination point to connect to other servers or untrusted environments. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the Filebeat and Metricbeat system.
Filebeat is a lightweight shipper for forwarding and centralizing log data. It monitors the log files or locations that you specify, collects log events, and forwards them either to Elisticsearch or Logstash for indexing.
Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. It helps you monitor your servers by collecting metrics from the system and services running on the server.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |  
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |  
| Web1     | Webserver | 10.0.0.5   | Linux            |  
| Web2     | Webserver | 10.0.0.6   | Linux            |  
| Web3     | Webserver | 10.0.0.7   | Linux            |  
| Web4     | ELK       | 10.1.0.4   | Linux            |  

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
205.68.104.10

Machines within the network can only be accessed by the Jump Box.
The home machine is allowed to access the ELK VM with an IP of 205.68.104.10

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |                                                                                                    

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because you will be able to deploy the same applecation out to thousands of machines while only needing to configure one file if anything changes. 

The playbook implements the following tasks:
- Download and installs Metricbeat/Filebeat
- Creates a config file
- Enables docker
- Setup, start, and persist connection on boot. 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](Elk-Stack/Diagrams/dockerps.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- filebeat-7.6.1-amd64.deb
- metricbeat-7.6.1-amd64.deb

These Beats allow us to collect the following information from each machine:
Filebeat is "A lightweight shipper for forwarding and centralizing log data". It helps  you keep the simple things simple by offering a lgihtweight way to forward and centralize logs and files. Metricbeat is a lightweight shipper for metrics. It collects metrics from your systems and sends system and service statistics. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to /etc/ansible/config.
- Update the config file to include the correct services and IPs
- Run the playbook, and navigate to the IP to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- Which file is the playbook? Where do you copy it? The metricbeat-playbook.yml and filebeat-playbook.yml are the files and you copy them to the ELK server.
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on? You would have to update the filebeat/metricbeat-config.yml file to run the playbooks on specific machines. To specify which machine to install the ELK server on you would have to configure the filebeat/metricbeat-playbook.yml.
- Which URL do you navigate to in order to check that the ELK server is running? You would go to your ELK server public IP address.

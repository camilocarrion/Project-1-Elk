## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.
Images/network-diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/roles/elkbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly redundant, in addition to restricting internet access to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box? Redundancy, the load balancer ensures that one work station/server is not over 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name                 | Function       | IP Address | Operating System |
|----------------------|----------------|------------|------------------|
| JumpBoxProvisionerV2 | Gateway        | 10.0.0.6   | Linux            |
| DVWA-VM1             | Workstation VM | 10.1.0.4   | Linux            |
| DVWA-VM2             | Workstation VM | 10.1.0.5   | Linux            |
| DVWA-VM3             | Elk Server     | 10.1.0.8   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Gateway machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-69.180.25.27

Machines within the network can only be accessed by _____.
-JumpboxProvisionerV2: Private 10.0.0.6, Public 52.255.183.13

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| JumpBoxProvisionerV2 | yes                 | 69.180.25.27         |
| DVWA-VM1             | no                  | 52.255.183.13        |
| DVWA-VM2             | no                  | 52.255.183.13        |
| DVWA-VM3             | no                  | 52.255.183.13        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It ensures consistent and efficient deployment of new machines as they are built or rebuilt.  

The playbook implements the following tasks:
- Install Docker.io.
- Install Python-pip.
- Install Docker Module through Python-pip.
- Increase Virtual memory to accommodate Elk processes.
- Install Elk Container, publich ports, set boot policy, and launch container.
 
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/docker_ps.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.4
- 10.1.0.5

We have installed the following Beats on these machines:
- Filebeats

These Beats allow us to collect the following information from each machine:
- Filebeat collects and directs log data to elasticsearch which then feeds it to the Kibana GUI. 
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat config file to /etc/ansible/files.
- Update the filebeat config file to include the private IP address of DVWA-VM3 
- Run the playbook, and navigate to http://52.177.149.147:5601 to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? The playbooks are elkbook.yml, basic_playbook.yml, and filebeat-install.yml.  The playbooks are located in the roles folder of ansible. 
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
        The "hosts" file in /etc/ansible dictates the groups for playbook implementation.  The elkservers group chooses the machines to install ELK servers while "webservers" decides the
- _Which URL do you navigate to in order to check that the ELK server is running? http://52.177.149.147:5601

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
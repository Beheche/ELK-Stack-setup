## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

../Network Diagram/Network_Diagram.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire
deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, 
such as Filebeat.

/etc/ansible/roles/filebeat.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly resilient, in addition to restricting traffic to the network.
What aspect of security do load balancers protect? DDoS attacks
What is the advantage of a jump box? Controls access to the other machines by allowing connections from specific IP addresses 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system network.
What does Filebeat watch for? Changes in file system
What does Metricbeat record? Machine metrics such as uptime and CPU usage

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name      | Function        | IP Address | Operating System |
|-----------|-----------------|------------|------------------|
| Jump Box  | Gateway         | 10.1.0.9   | Linux v18.06     |
| DVWA      | Web Application | 10.1.0.11  | Linux v18.06     |
| ELK Stack | Data Collection | 10.1.0.7   | Linux v18.06     |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP
addresses:
Add whitelisted IP addresses 23.120.57.138

Machines within the network can only be accessed by the jump box.
Which machine did you allow to access your ELK VM? jump box
What was its IP address?_ 10.1.0.9

A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|:-------------------:|----------------------|
| Jump Box  | No                  | 23.120.57.138        |
| DVWA      | Yes                 | Internet, 10.1.0.9   |
| ELK Stack | No                  | 10.1.0.9             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
What is the main advantage of automating configuration with Ansible?_ faster to recreate it onto another machine

The playbook implements the following tasks:
- installs docker.io
- installs python-pip to install docker
- increases virtual memory to hold the container
- downloads and launch the elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/Elk_Container.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
List the IP addresses of the machines you are monitoring_ 10.1.0.11

We have installed the following Beats on these machines:
Specify which Beats you successfully installed_ metricbeats

These Beats allow us to collect the following information from each machine:
In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat`
collects Windows logs, which we use to track user logon events, etc.
 - Metricbeats collects metric data such as CPU usage and uptime

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node
provisioned: 

SSH into the control node and follow the steps below:
- Copy the confinguration file to ansible files.
- Update the configuration file to include the internal IP address of container, username, and password
- Run the playbook, and navigate to the container to check that the installation worked as expected.

Which file is the playbook? Yml file in the roles directory
Which file do you update to make Ansible run the playbook on a specific machine? Ansible host file
How do I specify which machine to install the ELK server on versus which to install Filebeat on? The host name given in the playbook
Which URL do you navigate to in order to check that the ELK server is running? Public IP of virtual machine with the elk server

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc. 
 - ansible-playbook

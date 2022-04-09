## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Desktop/Diagrams/diagram_elkstack.jpeg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the filebeat-playbook.yml file may be used to install only certain pieces of it, such as Filebeat.



This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting overprocessing to the network.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics data.
-Filebeat monitor systems by capturing log data and events.
-Metricbeat collects the metric data from systems and includes data such as CPU, memory, etc.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.


| Name      | Function  | IP Address  | Operating System  |
|-----------|-----------|-------------|-------------------|
| Jump Box  | Gateway   | 10.0.0.10   | Linux             |
| ELK-Server| Log Server| 10.1.0.4    | Linux             |
| Web1      | Web Server| 10.0.0.8    | Linux             |
| Web2      | Web Server| 10.0.0.11   | Linux             |
| Web3      | Web Server| 10.0.0.13   | Linux             |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
-172.110.245.101

Machines within the network can only be accessed by SSH.


A summary of the access policies in place can be found in the table below.

| Name      | Publicly Accessible | Allowed IP Addresses |
|-----------|---------------------|----------------------|
| Jump Box  | Yes                 | 172.110.245.101      |
| ELK-Server| Yes                 | 172.110.245.101      |
| Web1      | No                  | 10.0.0.10            |
| Web2      | No                  | 10.0.0.10            |
| Web3      | No                  | 10.0.0.10            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
-It saves time with it being easy to configure multiple machines at the same time within the same ruleset.

The playbook implements the following tasks:

Install docker.io
Install python3.pip
Install docker module
Download and configure the ELK docker container
Run docker service automatically upon boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Desktop/Diagrams/diagram_elkstack.jpeg

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web1 10.0.0.8   
Web2 10.0.0.11   
Web3 10.0.0.13   

We have installed the following Beats on these machines:
Filebeat
Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeat will be used to collect log files from very specific files such as Apache, Microsoft Azure tools and web servers, MySQL databases. -Metricbeat will be used to monitor VM status, per CPU core stats, per filesystem stats, memory stats and network stats.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the elk-playbook.yml file to /etc/ansible/roles
- Update the host file to include...
- Run the playbook, and navigate to Kibana to check that the installation worked.


- Which file is the playbook? YAML file Where do you copy it?_
- Which file do you update to make Ansible run the playbook on a specific machine? Host file How do I specify which machine to install the ELK server on versus which to install Filebeat on?
- Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana
 
_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
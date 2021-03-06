## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1Fgr4H_7epeTuSUBmL_B6ErX5avHoV0Zh/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yaml file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: Enter the playbook file._

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting users to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system usage.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.
+----------+-----------------+--------------+---------------------+
| Name     | Function        | IP address   | Operating system    |
+----------+-----------------+--------------+---------------------+
| Jump Box | Gateway         | 20.98.77.236 | Ubuntu server 20.04 |
+----------+-----------------+--------------+---------------------+
| web-1    | DVWA web server | 10.0.0.10    | Ubuntu server 20.04 |
+----------+-----------------+--------------+---------------------+
| web-2    | DVWA web server | 10.0.0.11    | Ubuntu server 20.04 |
+----------+-----------------+--------------+---------------------+
| web-3    | DVWA web server | 10.0.0.12    | Ubuntu server 20.04 |
+----------+-----------------+--------------+---------------------+
| Elk-VM   | Elk Stack       | 10.1.0.4     | Ubuntu server 20.04 |
+----------+-----------------+--------------+---------------------+


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 67.164.185.149
- _TODO: Add whitelisted IP addresses_

Machines within the network can only be accessed by the Docker container on the Jump-box.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

A summary of the access policies in place can be found in the table below.
+------------+---------------------+------------------------------+
| Name       | Publicly Accessible | Allowed IP addresses         |
+------------+---------------------+------------------------------+
| Jump Box   | No                  | 67.164.185.149               |
+------------+---------------------+------------------------------+
| Web-1      | No                  | 20.98.77.236                 |
+------------+---------------------+------------------------------+
| Web-2      | No                  | 20.98.77.236                 |
+------------+---------------------+------------------------------+
| Web-3      | No                  | 20.98.77.236                 |
+------------+---------------------+------------------------------+
| Elk Server | No                  | 67.164.185.149, 20.98.77.236 |
+------------+---------------------+------------------------------+

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because... all virtual machines inside the virtual network will be identical.
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- The Elk installation playbook runs a curl command, to download docker on the Elk server.
- Second, the playbook installs python 3 pip.
- Then, the playbook sets the virtual memory on the Elk server to 262,144 bytes.
- After that, the playbook sets the docker container to start when the server is booted up.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://docs.google.com/document/d/1Qbn4CG4kbUfOWI-HzuBz_csWWlVdWISNDvAvq-eIBBo/edit?usp=sharing)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:10.0.0.10, 10.0.0.11
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines: filebeat, metricbeat
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
- Filebeat will collect system logs and for kibana.
- Metricbeat will collect information on how the system is running, ie. cpu usage, and ram usage.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to _____.
- Update the hosts file to include the webserver IP addresses
- Run the playbook, and navigate to the elk server and run "sudo docker ps" to check that the installation worked as expected. 

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it? install-elk.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ In the hosts file. Configure the [webservers]
to the private IP addresses of web-1 and web-2 (10.0.0.10, and 10.0.0.11 respectively). Add a line for [elk] and add the private IP of the elk server (10.1.0.4). In the header of the yaml scripts, the destination is defined.
For the Install-elk.yml file elk is the host. For the filebeat and metricbeat yaml files, webservers is the hosts 
- _Which URL do you navigate to in order to check that the ELK server is running? http://40.114.68.205:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._                                                                                                                       
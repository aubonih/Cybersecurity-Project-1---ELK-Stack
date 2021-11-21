# Cybersecurity-Project-1---ELK-Stack
Configuring a network via files that generate live ELK deployment on Azure. Done as a part of the 2021 UCLA Cybersecurity Bootcamp.

![test](https://github.com/aubonih/Cybersecurity-Project-1---ELK-Stack/blob/main/diagram.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml file may be used to install only certain pieces of it, such as Filebeat.

- [elk install](https://github.com/aubonih/Cybersecurity-Project-1---ELK-Stack/blob/main/yml%20playbooks/elk-playbook.yml)
- [filebeat](https://github.com/aubonih/Cybersecurity-Project-1---ELK-Stack/blob/main/yml%20playbooks/filebeat-playbook.yml)
- [metricbeat](https://github.com/aubonih/Cybersecurity-Project-1---ELK-Stack/blob/main/yml%20playbooks/metricbeat-playbook.yml)

This document contains the following details:

-Description of the Topology
-Access Policies
-ELK Configuration
 -Beats in Use
 -Machines Being Monitored
-How to Use the Ansible Build


**Description of the Topology**
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly responsive, in addition to restricting overload to the network.

Load balancing protects against DoS or DDoS attacks. Having a Jump Box prevents all machines in the network from being exposed to the public.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system metrics.

- Filebeat watches for log files, collects them, and forwards them to Elasticsearch or Logstash.
- Metricbeat records metric data from your system and services. i.e. CPU usage, memory, etc.

The configuration details of each machine may be found below.


| Name | Function | IP Address | Operating System |
|------|----------|------------|------------------|
|JumpBox      | Gateway         | 10.0.0.8           |   Linux              |
|Web-1      |    Web server      | 10.0.0.9           |       Linux           |
|Web-2      |   Web Server       | 10.0.0.10           |           Linux       |
|ELK Server      |  ELK-Stack        | 10.1.0.4           |             Linux     |




**Access Policies**
The machines on the internal network are not exposed to the public Internet.
Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

- Personal Public IP address

Machines within the network can only be accessed by SSH.

The ELK server was accessed from the JumpBox through port 5601.

A summary of the access policies in place can be found in the table below.


|Name | Publicly Accessible | Allowed IP Addresses |
| --- | --- | --- |
|JumpBox | No | Personal |
| Web-1 | No | 10.0.0.8 |
| Web-2 | No | 10.0.0.8 |
| ELK Server | No | 10.0.0.8 |


**Elk Configuration**
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

- Ansible is quick and simple to setup and use. No configuration was performed manually, which is advantageous because the services running can be limited, system installation and update can be streamlined, and processes are replicable as more machines are set up.

The playbook implements the following tasks:

- Install Docker, pip3, and Docker module
- Use sysctl to increase virtual memory
- Download and launch docker container for ELK server


**Target Machines & Beats**
This ELK server is configured to monitor the following machines:
- Web-1 10.0.0.9
- Web-2 10.0.0.10

We have installed the following Beats on these machines:

- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:

- Filebeat collects system logs, which can be used to track system events, etc.
- Metricbeat collects system and service metric data, which we can use to see CPU usage, etc.


**Using the Playbook**
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

- Copy the filebeat and metricbeat config files to /etc/ansible.
- Update the config file to include the ELK server's IP address
- Run the playbook, and navigate to http://[ELK-server-public-IP]:5601/app/kibana to check that the installation worked as expected.

- *Which file is the playbook?* filebeat-playbook.yml. metricbeat-playbook.yml
- *Where do you copy it?* /etc/ansible/filebeat-playbook.yml, /etc/ansible/metricbeat-playbook.yml
- *Which file do you update to make Ansible run the playbook on a specific machine?* /etc/ansible/hosts.cfg
- *How do I specify which machine to install the ELK server on* add a group [elk server] and the ELK server IP address, and the [web] group for the web servers
- *versus which to install Filebeat on?* update filebeat-config.yml. specify which machine to install by updating the host files with ip addresses of web/elk servers and selecting which group to run on in ansible
- *Which URL do you navigate to in order to check that the ELK server is running?* http://[ELK-server-public-IP:5601]/app/kibana

As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.
1. ssh RedAdmin@JumpBox(PrivateIP)
2. sudo docker container list -a - Locate the ansible container
3. sudo docker start (Funny_Name)
4. sudo docker attach (Funny_Name)
5. cd /etc/ansible
6. ansible-playbook elk-playbook.yml (Installs and Configures ELK-Server)
7. cd /etc/ansible/
8. ansible-playbook beats-playbook.yml (Installs and Configures Beats)
9. Open a new browser on Personal Workstation, navigate to http://[ELK-server-public-IP:5601]/app/kibana - This will bring up Kibana Web Portal

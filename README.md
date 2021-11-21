# Cybersecurity-Project-1---ELK-Stack
Configuring a network via files that generate live ELK deployment on Azure. Done as a part of the 2021 UCLA Cybersecurity Bootcamp.
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
| Web-2 | No | 10.0.08 |
| ELK Server | No | 10.0.0.8 |













Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

TODO: What is the main advantage of automating configuration with Ansible?

The playbook implements the following tasks:

TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc.
...
...

The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
Note: The following image link needs to be updated. Replace docker_ps_output.png with the name of your screenshot image file.


Target Machines & Beats
This ELK server is configured to monitor the following machines:

TODO: List the IP addresses of the machines you are monitoring

We have installed the following Beats on these machines:

TODO: Specify which Beats you successfully installed

These Beats allow us to collect the following information from each machine:

TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., Winlogbeat collects Windows logs, which we use to track user logon events, etc.


Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:
SSH into the control node and follow the steps below:

Copy the _____ file to _____.
Update the _____ file to include...
Run the playbook, and navigate to ____ to check that the installation worked as expected.

TODO: Answer the following questions to fill in the blanks:

Which file is the playbook? Where do you copy it?
Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?
_Which URL do you navigate to in order to check that the ELK server is running?

As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project13-Red-Team-Virtual Network](https://user-images.githubusercontent.com/96384289/159584883-0b0e8d75-adde-4c95-bc2b-a0d661b237b5.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

  - _Install elk_
  - _Filebeat-playbook_
  - _Metricbeat-playbook_

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- _Adding a Load Balancer helps ensure Availability as part of the CIA Triad in the event one of the VMs goes down._
- _A jumpbox allows for better management of the environment as the NSG was configured to allow inbound access to only one machine via an SSH key pair._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the sys logs and system system metrics.
- _Filebeat is used to collect log files and collect data about specific files on remote machines._
- _Metricbeat collects machine metrics such as uptime and CPU monitoring_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | Server   | 10.0.0.5   | Linux            |
| Web-2    | Server   | 10.0.0.6   | Linux            |
| Web-3-Elk| Server   | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _My personal IP address_

Machines within the network can only be accessed by the jumpbox.
- _The ELK VM was configured to be accessed via my personal workstation through Port 5601._

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | My public IP address |
| AZ LB    | Yes                 | My public IP address |
| Web-1    | No                  | 10.0.0.5             |
| Web-2    | No                  | 10.0.0.6             |
| Web-3-Elk| Yes                 | My public IP address |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _In this instance, Ansible allowed me to install DVWA on Web-1 and Web-2 by running one playbook rather than installing it on one VM at a time._

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web-1 10.0.0.5_
- _Web-2 10.0.0.6_

We have installed the following Beats on these machines:
- _I installed Filebeat and Metricbeat_

These Beats allow us to collect the following information from each machine:
- _Filebeat collects specific pieces of data about the file system such as agent.hostname, log.file.path, and process.pid to name a few.  Metricbeat collects metrics on the monitored machine such as uptime and CPU.  Several examples are system.network.out.packets and system.network.out.bytes._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to Web-1 and Web-2.
- Update the hosts file to include the IP address of the Webservers and Elk Server...
- Run the playbook, and navigate to Web-1, Web-2, and the Elk server to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

- _In order to check that the Elk Server is running go to http://[Elk_VM_Public_IP]:5601/app/kibana_

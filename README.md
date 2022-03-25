## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project13-Red-Team-Virtual Network](https://user-images.githubusercontent.com/96384289/159976770-cccdca5d-cf9d-4a0a-bd75-0f903419ca72.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YML file may be used to install only certain pieces of it, such as Filebeat.

  - [Install Elk](/ansible/ansible/install-elk.yml)
  - [Filebeat Playbook](/ansible/ansible/filebeat-playbook.yml)
  - [Metricbeat Playbook](/ansible/ansible/metricbeat-playbook.yml)

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

What aspect of security do load balancers protect?
- _Adding a Load Balancer helps ensure Availability as part of the CIA Triad in the event one of the VMs goes down._

What is the advantage of a jump box?
- _A jumpbox allows for better management of the environment as the NSG was configured to allow inbound access to only one machine via an SSH key pair._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the **sys logs** and system **metrics**.

What does Filebeat watch for?
- _Filebeat is used to collect log files and collect data about specific files on remote machines._

What does Metricbeat record?
- _Metricbeat collects machine metrics such as uptime and CPU monitoring_

The configuration details of each machine may be found below.

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

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because?
- _In this instance, Ansible allowed me to install DVWA on Web-1 and Web-2 by running one playbook rather than installing it on one VM at a time._

The playbook implements the following tasks:
- _Installs docker.io, pip3, and docker python module using the install-elk.yml file._
- 
- ...
- ...

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Project13-Web3-Elk_Container](https://user-images.githubusercontent.com/96384289/159979739-5a7f9331-a829-41ea-8f64-4f7d6e4310a1.jpeg)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _Web-1 10.0.0.5_
- _Web-2 10.0.0.6_

We have installed the following Beats on these machines:
- _Filebeat_
- _Metricbeat_

These Beats allow us to collect the following information from each machine:
- _Filebeat collects specific pieces of data about the file system such as agent.hostname, log.file.path, and process.pid to name a few._ 

The below screenshot shows filebeat traffic on the Elk server.

![Project13-Filebeat_traffic](https://user-images.githubusercontent.com/96384289/160025715-e8a1e61c-b5f2-4fd7-aa14-d3717f411d36.jpeg)


- _Metricbeat collects metrics on the monitored machine such as memory and CPU._

The below screenshot shows metricbeat traffic on the Elk server.

![Project13-Kibana_metricbeat_traffic](https://user-images.githubusercontent.com/96384289/160026234-3c19f28b-5dce-43dc-8026-6bbdbdd1d900.jpeg)


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to Web-1 and Web-2.
- Update the hosts file to include the IP address of the Webservers and Elk Server...
- Run the playbook, and navigate to Web-1, Web-2, and the Elk server to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_

- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

- In order to check that the Elk Server is running go to _http://20.114.247.86:5601/app/kibana_

![Project13-Kibana_Confirm](https://user-images.githubusercontent.com/96384289/160026533-28b5ae1c-4b2b-4451-9c39-c8f1f7f5428c.jpeg)





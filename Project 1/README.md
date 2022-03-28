# Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](Diagrams/Gaurav's%20HW%2013.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the file may be used to install only certain pieces of it, such as Filebeat.

  - [DVWA Webserver Playbook](Scirpts/Ansible/playbook.yml)
  - [ELK Stack Playbook](Scirpts/ELK/install-elk.yml)
  - [Filebeat Playbook](Scirpts/Filebeat/Filebeat-playbook.yml)
  - [Metricbeat Playbook](Scirpts/Metricbeat/metricbeat-playbook.yml)
   

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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log fileas and system system.

The configuration details of each machine may be found below.

| Name                 | Function           | Private IP Address | Public IP Address | Operating System |
|----------------------|--------------------|--------------------|-------------------|------------------|
| JumpBox-Provisioner  | Gateway            | 10.0.0.8           | 20.58.182.52      | Ubuntu LTS 18.04 |
| Web-1                | Application Server | 10.0.0.9           | N/A               | Ubuntu LTS 18.04 |
| Web-2                | Application Server | 10.0.0.10          | N/A               | Ubuntu LTS 18.04 |
| RedTeam-ELK-NSG      | ELK Stack          | 10.2.0.4           | 20.70.89.40       | Ubuntu LTS 18.04 |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox-Provisioner and RedTeam-ELK-NSG (Kibana) machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My Local Machine IP Address(101.117.19.35)

Machines within the network can only be accessed by JumpBox-Provisioner.

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses |
|----------------------|---------------------|----------------------|
| JumpBox-Provisioner  | Yes                 | 101.117.19.35        |
| RedTeam-ELK-NSG      | Yes                 | 101.117.19.35        |
| Web-1                | No                  | 10.0.0.8             |
| Web-2                | No                  | 10.0.0.8             |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous 
because it allows a consistent and predictable configuration. Also, with an automated setup, the ELK stack
can be created and configured very quickly.

The playbook implements the following tasks:
- Configure maximum mapped memory with -sysctl module
- Install -docker.io and -python3-pip packages with -apt module
- Install docker -python package with -pip
- Enable systemd docker service
- Run ELK docker container 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](Diagrams/elk.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1: 10.0.0.9
- Web-2: 10.0.0.10


We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat allows system logs from the Webserver(VMs) to the ELK Stack in an easy to read format.
- Metricbeat provides system and service statistics about the Web-VMs to the ELK stack VM.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/files.
- Update the /etc/ansible/hosts file to include the ELK stack Vm IP Add.
- Run the playbook, and navigate to http://20.70.89.40:5601/app/kibana#/home.

![](Diagrams/Kibana.png)

![](Scirpts/Filebeat/filebeat.png)

![](Scirpts/Metricbeat/metricbeat.png)




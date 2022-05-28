# KN_Bootcamp_Project_1

Week 13 Project 1 for Bootcamp

Description

This project was set out to configure an ELK stack server in order to set up a cloud monitoring system. It resulted in tangible deliverables that demonstrate knowledge of cloud, network security, logging and monitoring. 

The files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/72707835/170837555-d3f0f683-4b6c-4dfb-9eec-6ca123393aed.png)

**This document contains the following details:**

1. Description of the Topology

2. Access Policies

3. ELK Configuration

		3.1 Beats in Use

		3.2 Machines Being Monitored

4. How to Use the Ansible Build


**Description of the Topology**

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load Balancing ensures that the application will be highly responsive, in addition to restricting connection to the network. The advantage of a Jumpboxprovisioner is that restricts access and acts as a gateway for ssh connections in the live enviorment.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the CPU and system Logs.

Filebeat is used for collecting log events of the server it is installed on._
MetricBeat is Collects Operation System Metrics such as CPU load, Network Traffic and other related fields.
The configuration details of each machine may be found below.







Name	Function	IP Address	Operating System
JumpBoxProvisioner	10.0.0.4	Linux
WEB-1	Redunant web server 1	10.0.0.5	Linux
WEB-2	Redunant web server 2	10.0.0.6	Linux
ELKVM  STACK	10.1.0.4	Linux
Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Load Balancer machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Port 80 (TCP over HTTP)
Machines within the network can only be accessed by Ansible Container via the JumpBoxProvisioner using Port 22.

JumpBoxProvisioner IP 10.0.0.4
Name	Publicly Accessible	Allowed IP Addresses
Jump Box	NO	10.0.0.4
WEB_1	YES	10.0.0.8
WEB_2	YES	10.0.0.9
WEB_3	YES	10.0.0.5
ELK	NO	10.1.0.4
Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

The advantage of automating configurations with Ansible is efficint synchronicity in deployment across all systems
The playbook implements the following tasks:

Checks and installs Docker.io
Checks and installs Python3-pip
Checks and installs Docker Module (python)
Checks and downloads, and run elk container with published ports
Enable docker service on boot
Increase virtual memory
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance

Elk-container-screenshot.png

Target Machines & Beats
This ELK server is configured to monitor the following machines:

Name	Allowed IP Addresses
WEB_1	10.0.0.8
WEB_2	10.0.0.9
WEB_3	10.0.0.5
We have installed the following Beats on these machines:

Fileboat
Metricbeat
These Beats allow us to collect the following information from each machine:

Filebeat collects log files and system logs
Matricbeat collects metric for CPU Network and other related services
Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

configELK.yml is the ansible-playbook copied from install-elk.yml

curl https://columbia.bootcampcontent.com/columbia-bootcamp/CU-VIRT-CYBER-PT-02-2022-U-LOL/-/raw/main/13-ELK-Stack-Project/Activities/Stu_Day_1/Unsolved/Resources/install-elk.yml > configELK.yml

Updated the hosts file to include the ELK-VM under the category elk

nano /etc/ansible/hosts add [elk] and 10.1.0.4

Run the playbook, and navigate to 20.242.81.178:5601 to check that the installation worked as expected.

On CLI local host (if unix-based) open 20.242.81.178:5601

As a Bonus, provide the specific commands the user will need to run to download the playbook, update the files, etc.

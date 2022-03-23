## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](https://github.com/contrariar/Project-1-ELK/blob/main/elk%20diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

  - /etc/ansible/install-elk-playbook.yml   

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly efficient, in addition to restricting traffic to the network.
-  What aspect of security do load balancers protect?
- 1. LB protect from DDOS. 
- 2. Increase the availability  of the network  
-  What is the advantage of a jump box?
-  Provide access to the user form a single node(conection) that is secure and it can be monitored 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log and system traffic.
-  What does Filebeat watch for? 
- A. It watches for the logs files and events
-  What does Metricbeat record?
- A. Metricbeat periodically collect metric data from your target servers.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Web1     | Server   | 10.0.0.7   | Ubuntu           |
| Web2     | Server   | 10.0.0.8   | Ubuntu           |
| ELK      | Server   | 10.0.0.4   | Ubuntu           |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Add whitelisted IP addresses 
- A. 76.108.225.8

Machines within the network can only be accessed by SSH
- Which machine did you allow to access your ELK VM?
- A. JumpBoxPro What was its IP address? 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
| Web1     | No                  | 10.0.0.7             |
| Web2     | NO                  | 10.0.0.8             |
| ELK      | Yes                 | 10.0.0.4             |  



### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?_
 A. This allows you to deploy to multiple servers using a single playbook
The playbook implements the following tasks:
-  In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
-  1. Install docker.io
-  2. Install pip3
-  3. Install Docker python module
-  4. Use more memory
-  5. download and launch a docker elk container


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](https://github.com/contrariar/Project-1-ELK/blob/main/docker%20ps.JPG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- List the IP addresses of the machines you are monitoring_
-  A.  Web1 10.1.0.7 Web2 10.1.0.8

We have installed the following Beats on these machines:
- Specify which Beats you successfully installed_
- A.  Filebeat & Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
A. Filebeat:  monitors log files and locations, collects log event
   Metricbeat:  collects metrics from the operating system .
   
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to /etc/ansible.
- Update the configuration file to include the webservers and ElkVM private Ip addres
- 
- Run the playbook, and navigate to ElkVM to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?
- A. /etc/ansible/file/filebeat-configuration.yml
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_ 
- A.  filebeat-config.yml | update the host files with ip addresses of elk servers and selecting which group to run on in ansible.
- _Which URL do you navigate to in order to check that the ELK server is running? http://[your.ELK-VM.External.IP]:5601/app/kibana

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![ScreenShot](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Diagrams/Network-Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Playbookscripts file may be used to install only certain pieces of it, such as Filebeat.

[Ansible Playbook](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Ansible/Ansible-Playbook)

[ELK Installation Playbook](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Ansible/ELK-Installation)

[Filebeat Playbook](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Ansible/Filebeat-Playbook.txt)

[Metricbeat](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Ansible/Metricbeat-Playbook)

[Filbeat Configuration](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Ansible/Filebeat-Config)

[Metricbeat Configuration](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Ansible/Metricbeat-Config)

[Hosts File](https://github.com/Fischer-Maris/University-of-Richmond-CyberSecurity-Projects/blob/ed19dec/Ansible/hosts)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.

What aspect of security do load balancers protect?
Answer: Availability, Web Traffic, Web Security

What is the advantage of a jump box?
Answer: Automation, Security, Network Segmentation, Access Control

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat monitors, locates and ships log data.
- Metricbeat outputs metrics and statistics to help monitor servers.

The configuration details of each machine may be found below.

| Name        | Function   | IP Address | Operating System |
|-------------|------------|------------|------------------|
| Jump Box    | Gateway    | 10.0.0.1   | Linux            |
| Web-1       | Webserver  | 10.0.0.7   | Linux            |
| Web-2       | Webserver  | 10.0.0.8   | Linux            |
| Django-VM-1(ELKserver) | Monitoring | 10.1.0.4   | Linux            |
  
  
### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Elk Sever machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Workstation Public IP through TCP 5601

Machines within the network can only be accessed by Workstation and JumpBox.
Which machine did you allow to access your ELK VM? What was its IP address?
- Jump-Box-Provisioner IP:10.0.0.1 via SSH port 22
- Workstation Public IP via port TCP 5601
A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses              |
|------------|---------------------|-----------------------------------|
| Jump Box   | No                  | Workstation Public IP on SSH 22   |                 
| Web-1      | No                  | 10.0.0.7 on SSH 22                |
| Web-2      | No                  | 10.0.0.8 on SSH 22                |
| ELK-Server | No                  | Workstation Public IP on TCP 5601 |
| Load Balancer      | No                  | Workstation Public IP on HTTP 80  |
                                                         

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible lets you quickly and easily deploy multitier apps. You won't need to write custom code to automate your systems; you list the tasks required to be done by writing a playbook, and Ansible will figure out how to get your systems to the state you want them to be in.

The playbook implements the following tasks:

- Specify a different group of machines as well as a different remote user
```html
-name: Config elk VM with Docker:
 hosts: elk
 remote_user: azadmin
 tasks:
 ```
 
 - Increase System Memory :
 ```html
- name: Use more memory
 sysctl:
   name: vm.max_map_count
   value: '262144'
   state: present
   reload: yes
```

- Install the following services:
```html
   `docker.io`
   `python3-pip`
   `docker`, which is the Docker Python pip module.
```

- Launching and Exposing the container with these published ports:
```html
 `5601:5601` 
 `9200:9200`
 `5044:5044`
```

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![markdown Logo]()


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._



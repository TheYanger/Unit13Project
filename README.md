## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/RedTeamDiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Deployment.yml file may be used to install only certain pieces of it, such as Filebeat.


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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system files.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    | WebHost  | 10.0.0.5   | Linux            |
| Web-2    | WebHost  | 10.0.0.6   | Linux            |
| Web-3    | WebHost  | 10.0.0.7   | Linux            |
| Elk      | Kibana   |13.77.165.3 | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 73.12.236.91

Machines within the network can only be accessed by 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 73.12.236.91         |
| Web-VMs  | No                  | 10.0.0.4             |
| Elk      | Yes                 | 73.12.236.91         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it ensures we can reconfigure the server to it's desired state quickly and accurately whenever needed, as well as spin up new servers to the exact specification at will.

The playbook implements the following tasks:
-Installs Docker
-Configures hosts file to connect to Web VMs
-Downloads and configures Filebeat from image
-Downloads and configures Metricbeat from image

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Note: The instructions did not indicate we needed to screenshot this step, I don't have a screenshot of that command running, I have many other screenshots, included is one after running the .yml](ElkInstall.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5
- 10.0.0.6
- 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Log Data as well as traffic metrics
- Changes to file structure and access attempts

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the FilebeatConfig.yml file to etc/ansible/files/.
- Update the hosts file to include the IP address of the new machine as an Elk server.
- Run the playbook, and navigate to http://13.77.165.3:5601/app/kibana to check that the installation worked as expected.


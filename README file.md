## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![](https://github.com/Anise94/Secure-Cloud-Network-using-ELK-stack/blob/main/Images/Cloud%20Network%20with%20ELK%20Stack.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible YAML file may be used to install only certain pieces of it, such as Filebeat.

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

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system services.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Web-1    |          | 10.0.0.5   | Linux            |
| Web-2    |          | 10.0.0.6   | Linux            |
| Elk      |          | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 174.63.52.153

Machines within the network can only be accessed by the Jump Box VM 10.0.0.4.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 174.63.52.153        |
| Web-1    | No                  | 10.0.0.4             |
| Web-2    | No                  | 10.0.0.4             |
| ELK      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually. The advantage that comes with automation is that multiple machines can be configured consistently and quickly. In this scenario of a single machine the time savings was small but in a scenario where hundreds or thousands of machines are to be configured the time savings is of considerable value.

The playbook implements the following tasks:
- Istall docker.io
- Install python3-pip
- Install Docker module
- Increase virtual memory
- Use more memory
- download and launch a docker elk container
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![](https://github.com/Anise94/Secure-Cloud-Network-using-ELK-stack/blob/main/Images/ELK%20VM%20with%20docker%20ps%20command.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines: 10.0.0.5, 10.0.0.6

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- system log data - for example data from invalid/accepted ssh logins
- system metric data - for example CPU usage and system load 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Configure Elk VM with Docker YAML playbook file to your ansible directory.
- Update the hosts file to include the internal IP of the VM you intend to install the ELK server on. Add the IP address under the section [elk]. (section can be added to the file if it isn't already there.

![](https://github.com/Anise94/Secure-Cloud-Network-using-ELK-stack/blob/main/Images/Hosts%20file%20-%20elk%20section.png)

- Run the playbook (ansible-playbook Configure Elk VM with Docker YAML playbook)
- Navigate to 'http://<ELK.VM.External.IP>:5601/app/kibana' to check that the installation worked as expected.

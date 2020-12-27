## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

### My cloud image
![alt twxt](https://github.com/Lola-CS/CyberSecurity-BCS/blob/main/Images/Untitled%20Diagram.io%20HWork12.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook_found in ./Playbooks file may be used to install only certain pieces of it, such as Filebeat.

  -: Playbooks located in./Playbooks

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availability and reliablility by sending request only to servers that are online, in addition to restricting unwanted access to the network.
What aspect of security do load balancers protect? What is the advantage of a jump box?Load balancers protects the system from DDoS attacks by shifting attack traffic.The advantage of jump box is to give access to the user from a 
single node that can be secured and monitored.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
 What does Filebeat watch for? log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
 What does Metricbeat record? metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  |  10.1.0.7  | Linux            | 
| Web-1	   | DVWA     |  10.1.0.5  | Linux            |
| Web-2	   | DVWA     |  10.1.0.6  | Linux            |
| Web-3    | DVWA     |  10.1.0.8  |  Linux           |

### Access Policies
 
The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box  machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: My public IP address 

Machines within the network can only be accessed by ansible container located in my Jump box.
Elk machine can only be acces by ansible container inside JUmp box on port22- ssh. Kibana webserver can be access by my public IP on port 80. IP of ELK machine is this 20.190.62.15.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 10.0.0.1 10.0.0.2    |
| Web-1    |  No                 |    10.1.0.7          |
| Web-2    |  No                 |    10.1.0.7          |
| Web-3    |  No                 |    10.1.0.7          |
| Elk-VM   |  No -ssh            |    10.1.0.7          | 
| Elk-VM   |  Yes-http           | My public IP address |
  

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it allows IT administrators to automate away the drudgery from their daily task.

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
- Install docker.io and paython docker "pip3"
- vm.max_map_count to use more ram "262144"
- download and launch a docker elk container . sebp/elk: "761"
- forward ports from container to host       5601:5601 
                                             9200:9200
                                             5044:5044

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![alt twxt] (Images/docker_proof.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_ Filebeat/Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

Fileabeat collects Log files, which we use to monitore the Elasticsearch log files to colletc log events and then ship them to monitoring cluster.Recent Logsare visible on the monitoring page in Kibana.Verifies that Elasticsearch is running and the
 monitoring cluster is ready to recive data from Filebeat.
Metricbeat collects Metrics and statistics that collects and ships them to the output Elasticsearch or Logstash.Metricbeat helps monitor servers by collecting metrics from the system and services runing on the server: Apache, HAPRoxy,MongoDb and ect.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a In order to use the playbook,  

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
# Cloud Computing Lab

This repository contains the practical work completed as part of the Cloud Computing Laboratory. It covers virtual machine configuration, network connectivity, network topology creation, and Software-Defined Networking (SDN) implementation using open-source tools.

---

# Experiment 1 — Virtual Machine Setup and Configuration

## Overview

This experiment focuses on creating, configuring, and verifying an Ubuntu Virtual Machine using Oracle VirtualBox.

## Objective

To install and configure an open-source hypervisor, create an Ubuntu Virtual Machine, configure its virtual hardware resources, verify that the VM runs successfully, and install the required build tools and Linux kernel headers.

## Software and Environment

| Parameter | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Guest Operating System | Ubuntu |
| Architecture | 64-bit |
| Virtual Machine | Ubuntu 26.04 |
| Network Mode | NAT |
| Virtual CPU | 3 CPUs |
| Base Memory | 4096 MB |
| Virtual Hard Disk | 25 GB |

## Tasks Completed

### Task 1 — Install Oracle VirtualBox
Installed and configured Oracle VirtualBox, an open-source virtualization platform used to create and manage virtual machines.

### Task 2 — Create a New Virtual Machine
Created a new virtual machine with the following configuration:

- VM Name: Ubuntu 26.04
- Operating System: Linux
- Distribution: Ubuntu
- Version: Ubuntu (64-bit)

### Task 3 — Configure the Virtual Machine

Configured the virtual hardware resources:

- CPU: 3 processors
- RAM: 4096 MB
- Storage: 25 GB virtual hard disk
- Network: NAT

### Task 4 — Configure VM Hardware
Verified the CPU, memory, storage, and network configuration through Oracle VirtualBox settings.

### Task 5 — Configure Ubuntu Installation
Selected the Ubuntu ISO image and configured the required options for creating the Ubuntu virtual machine.

### Task 6 — Start the Virtual Machine
Started the Ubuntu virtual machine and proceeded with the boot process.

### Task 7 — Verify Ubuntu VM
Verified that the Ubuntu virtual machine successfully booted and the Ubuntu desktop environment was accessible.

### Task 8 — Install Required Build Tools

```bash
sudo apt update
sudo apt install -y build-essential linux-headers-$(uname -r)
```

---

# Experiment 2 — VM Cloning and Network Connectivity

## Overview

This experiment demonstrates the cloning of an Ubuntu Virtual Machine using Oracle VirtualBox and establishing network connectivity between the original and cloned virtual machines.

Both VMs are connected to a customized NAT Network, allowing them to communicate with each other through their assigned IP addresses.

## Objective

- Clone an existing Ubuntu Virtual Machine.
- Create and configure a customized NAT Network.
- Connect both VMs to the same NAT Network.
- Verify the network interface and IP configuration.
- Verify communication between the VMs using the `ping` command.
- Verify successful two-way connectivity through packet transmission.

## Tools and Technologies

- Oracle VirtualBox
- Ubuntu Linux
- NAT Network
- Linux Networking Commands

## Network Configuration

| Parameter | Configuration |
|---|---|
| Network Type | NAT Network |
| Network Name | MyNatNetwork |
| IPv4 Network | 10.0.2.0/24 |
| DHCP | Enabled |
| Network Interface | enp0s3 |

Both the original and cloned Ubuntu VMs were connected to the same `MyNatNetwork`.

## VM Configuration

### Original VM

- Attached to: NAT Network
- Network Name: MyNatNetwork
- Virtual Cable: Connected

### Useful Networking Commands

Check network interfaces and IP addresses:

```bash
ip a
```

Test connectivity between the virtual machines:

```bash
ping <destination-ip>
```

Stop the ping process:

```bash
Ctrl + C
```

---

# Experiment 3 — Creation of a Simple Network Topology Using Open-Source Network Virtualization Tools

## Overview

This experiment demonstrates the creation, configuration, and testing of different network topologies using Mininet, an open-source network virtualization tool running on an Ubuntu Linux Virtual Machine.

The experiment focuses on creating Single-Switch, Tree, and Linear topologies and verifying communication between virtual network nodes using basic Linux networking commands.

## Objective

To create and configure simple network topologies using Mininet and verify communication between virtual network nodes using basic Linux networking commands.

## Tools Used

- Ubuntu Linux
- Oracle VirtualBox
- Mininet
- Open vSwitch

## Mininet Installation and Setup

Mininet was installed along with its required dependencies using the Ubuntu package manager.

### Installation

```bash
sudo apt update
sudo apt install mininet -y
```

### Verify Installation

```bash
mn --version
```

### Clean Previous Mininet Configurations

```bash
sudo mn -c
```

---

# Experiment 4 — Implementation of Software-Defined Networking Using Ryu, Mininet and Open vSwitch

## Overview

This experiment demonstrates the implementation of a Software-Defined Networking (SDN) environment using the Ryu SDN Controller, Mininet and Open vSwitch.

A single-switch topology containing three hosts is created in Mininet. The Ryu controller manages the virtual switch using OpenFlow 1.3. Host connectivity is tested, switch flow-table entries are inspected, and a traffic-filtering rule is added and removed using Open vSwitch commands.

## Objective

- Configure an SDN environment using open-source tools.
- Install and configure the Ryu SDN Controller.
- Create a virtual network topology using Mininet.
- Establish communication between the Ryu controller and Open vSwitch.
- Verify connectivity between virtual hosts.
- Inspect OpenFlow flow-table entries.
- Demonstrate traffic filtering using a drop rule.

## Tools and Technologies

| Component | Technology |
|---|---|
| Operating System | Ubuntu Linux |
| Virtualization Platform | Oracle VirtualBox |
| Network Emulator | Mininet |
| Virtual Switch | Open vSwitch |
| SDN Controller | Ryu 4.34 |
| Communication Protocol | OpenFlow 1.3 |
| Python Version | Python 3.9.25 |

## 1. Update Ubuntu and Install Required Packages

Update the Ubuntu package index:

```bash
sudo apt update
```

Upgrade installed packages:

```bash
sudo apt upgrade -y
```

Install the required utilities:

```bash
sudo apt install -y git curl ca-certificates build-essential
```

Install Mininet, Open vSwitch and Python tools:

```bash
sudo apt install -y mininet openvswitch-switch python3 python3-pip python3-venv
```

## 2. Start and Verify Open vSwitch

Enable and start the Open vSwitch service:

```bash
sudo systemctl enable --now openvswitch-switch
```

Check the service status:

```bash
sudo systemctl status openvswitch-switch
```

Display the Open vSwitch configuration:

```bash
sudo ovs-vsctl show
```

## 3. Install Python 3.9 Using uv

Install `uv`:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Refresh the terminal environment if necessary:

```bash
source ~/.bashrc
```

Install Python 3.9:

```bash
uv python install 3.9
```

Verify the Python installation:

```bash
uv python find 3.9
```

## 4. Create and Activate a Python Virtual Environment

Create a virtual environment using Python 3.9:

```bash
uv venv --python 3.9 ~/ryu-env39
```

Activate the environment:

```bash
source ~/ryu-env39/bin/activate
```

Verify the Python version:

```bash
python --version
```

Expected version: Python 3.9.25.

Install compatible packaging tools:

```bash
uv pip install --python ~/ryu-env39/bin/python setuptools==57.5.0 wheel
```

## 5. Install the Ryu SDN Controller

Clone the Faucet-maintained Ryu repository:

```bash
git clone --branch v4.34 https://github.com/faucetsdn/ryu.git ~/ryu-source
```

Move into the source directory:

```bash
cd ~/ryu-source
```

Install Ryu:

```bash
python setup.py install
```

Install the required runtime dependencies:

```bash
uv pip install --python ~/ryu-env39/bin/python eventlet msgpack netaddr oslo.config ovs routes six tinyrpc webob
```

Use a compatible Eventlet version to resolve the `ALREADY_HANDLED` import issue:

```bash
uv pip install --python ~/ryu-env39/bin/python eventlet==0.30.2
```

## 6. Verify the Ryu Installation

Check the Ryu version:

```bash
ryu-manager --version
```

Expected output:

```text
ryu-manager 4.34
```

Verify the OpenFlow 1.3 application:

```bash
python -c "import ryu.app.simple_switch_13; print('OpenFlow 1.3 application OK')"
```

Expected output:

```text
OpenFlow 1.3 application OK
```

## 7. Start the Ryu Controller

Open a separate terminal and activate the virtual environment:

```bash
source ~/ryu-env39/bin/activate
```

Start the Ryu controller with the OpenFlow 1.3 learning-switch application:

```bash
ryu-manager --ofp-tcp-listen-port 6653 ryu.app.simple_switch_13
```

Keep this terminal running while using Mininet.

The controller listens on port `6653`.

## 8. Create the Mininet Topology

Open another terminal and clean previous Mininet configurations:

```bash
sudo mn -c
```

Create a single-switch topology with three hosts and a remote Ryu controller:

```bash
sudo mn --topo single,3 --controller=remote,ip=127.0.0.1,port=6653 --switch ovsk,protocols=OpenFlow13
```

The topology contains:

- Three hosts: h1, h2 and h3
- One Open vSwitch switch: s1
- One remote controller: Ryu
- Communication protocol: OpenFlow 1.3

## 9. Verify the Network Topology

Inside the Mininet CLI, list the available nodes:

```bash
nodes
```

Display the network connections:

```bash
net
```

The expected topology is:

```text
h1 --- s1
h2 --- s1
h3 --- s1
```

## 10. Test Host Connectivity

Test connectivity between all hosts:

```bash
pingall
```

Test communication between two individual hosts:

```bash
h1 ping h2
```

Stop the continuous ping using:

```text
Ctrl + C
```

A successful ping test indicates that the hosts can communicate through the virtual switch.

## 11. Inspect OpenFlow Flow Tables

Open a separate Ubuntu terminal, not the Mininet CLI.

Display the flow-table entries of switch `s1`:

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

This command displays the installed OpenFlow rules, priorities, packet counters, byte counters and forwarding actions.

## 12. Add a Traffic-Filtering Rule

Add a high-priority drop rule for traffic entering through port 1 of switch `s1`:

```bash
sudo ovs-ofctl -O OpenFlow13 add-flow s1 "priority=100,in_port=1,actions=drop"
```

The rule instructs the switch to drop matching incoming traffic instead of forwarding it.

Inspect the updated flow table:

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

The output should contain a rule similar to:

```text
priority=100,in_port="s1-eth1" actions=drop
```

## 13. Remove the Traffic-Filtering Rule

Remove the installed flow entries:

```bash
sudo ovs-ofctl -O OpenFlow13 del-flows s1
```

Inspect the flow table again:

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

## 14. Exit and Clean Up

Exit the Mininet CLI:

```bash
exit
```

Clean up Mininet configurations:

```bash
sudo mn -c
```

Stop the Ryu controller by pressing:

```text
Ctrl + C
```

## Important Execution Notes

- Keep the Ryu controller running before starting the Mininet topology.
- Use separate terminals for the Ryu controller, Mininet and Open vSwitch commands.
- Commands such as `nodes`, `net`, `pingall` and `h1 ping h2` must be executed inside the Mininet CLI.
- Commands such as `ovs-ofctl` must be executed in the Ubuntu terminal.
- If Mininet reports that it cannot contact the remote controller, verify that Ryu is running and listening on port `6653`.
- The drop rule uses switch port 1 (`s1-eth1`), which is connected to host `h1` in this topology.

## Results and Observations

- Successfully configured the Ryu SDN Controller.
- Created a three-host, single-switch Mininet topology.
- Connected the virtual switch to the remote Ryu controller using OpenFlow 1.3.
- Verified host connectivity using `pingall` and individual ping commands.
- Inspected the OpenFlow flow table using `ovs-ofctl`.
- Added and removed a traffic-filtering drop rule.

## Conclusion

The experiment demonstrates the implementation of a basic Software-Defined Networking environment using Ryu, Mininet and Open vSwitch. It provides practical experience in controller configuration, network topology creation, host connectivity testing and OpenFlow flow-table management.

---

## Repository Structure

```text
Cloud-Computing-Lab/
│
├── Experiment-1/
│   └── Virtual Machine Setup and Configuration
│
├── Experiment-2/
│   └── VM Cloning and Network Connectivity
│
├── Experiment-3/
│   └── Mininet Network Topology Creation
│
└── Experiment-4/
    └── SDN Implementation Using Ryu and Mininet
```
# ☁️ Cloud Computing Lab 6
## Familiarization and Usage of Cloud Services Using AWS and Open-Source Cloud Tools

![Cloud Computing](https://img.shields.io/badge/Domain-Cloud%20Computing-blue)
![AWS](https://img.shields.io/badge/Cloud-AWS-orange)
![Ubuntu](https://img.shields.io/badge/OS-Ubuntu-E95420)
![VirtualBox](https://img.shields.io/badge/Virtualization-Oracle%20VirtualBox-blue)

## 📌 Aim

To become familiar with different cloud services and perform basic cloud operations using **Amazon Web Services (AWS), Ubuntu Linux, Oracle VirtualBox, and AWS Command Line Interface (CLI).**

## 🛠️ Technologies & Tools Used

- **Amazon Web Services (AWS)**
- Ubuntu Linux
- Oracle VirtualBox
- Amazon S3
- AWS IAM
- Amazon EC2
- Amazon VPC
- Amazon CloudWatch
- AWS CLI / AWS CloudShell

## 📚 Experiment Overview

This experiment is divided into four major practical tasks.

| Task | Practical Area | Description |
|---|---|---|
| 1 | Virtual Machine Setup | Install Ubuntu using Oracle VirtualBox and perform basic Linux operations. |
| 2 | Cloud Storage | Create an Amazon S3 bucket and perform file upload, download and deletion. |
| 3 | Cloud Service Exploration | Explore IAM, EC2 and VPC services through AWS Console. |
| 4 | Monitoring & CLI | Explore CloudWatch and execute basic AWS CLI commands. |

---

## 🖥️ Task 1: Virtual Machine Setup

**Objective:** Set up an Ubuntu virtual machine using Oracle VirtualBox.

### Steps Performed

1. Create a virtual machine in Oracle VirtualBox.
2. Install Ubuntu Linux.
3. Update the package lists and installed packages.
4. Install basic utilities.
5. Execute basic Linux terminal commands.

### Commands

```bash
sudo apt update
sudo apt upgrade -y
```

---

## 🪣 Task 2: Cloud Storage Using Amazon S3

**Objective:** Understand object storage and perform basic storage operations using Amazon S3.

Amazon S3 (Simple Storage Service) is an object storage service used to store and retrieve data over the internet.

### Steps Performed

1. Access the AWS Management Console.
2. Search for and open Amazon S3.
3. Create a globally unique S3 bucket.
4. Select the appropriate AWS Region.
5. Keep Block Public Access enabled.
6. Retain default encryption settings.
7. Create a sample text file in Ubuntu.
8. Upload the file to the S3 bucket.
9. Download the uploaded object.
10. Verify its contents and delete the test object and empty bucket.

### Create a Sample File

```bash
mkdir cloud-lab6
cd cloud-lab6

echo "Cloud Computing Lab Experiment 6" > lab-note.txt

cat lab-note.txt
```

### Expected Result

A private S3 bucket is created successfully, and a sample file is uploaded, downloaded, verified and deleted.

---

## 🔐 Task 3A: Identity and Access Management (IAM)

**Objective:** Understand how AWS manages access to cloud resources.

AWS IAM (Identity and Access Management) controls who can access AWS services and what actions they can perform.

### Concepts Explored

- **Users:** Identities representing users.
- **Groups:** Collections of IAM users.
- **Roles:** Identities that provide temporary permissions.
- **Policies:** Documents defining allowed or denied actions.

### Example IAM Policy

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket"
      ],
      "Resource": "arn:aws:s3:::example-bucket"
    }
  ]
}
```

**Principle of Least Privilege:** Every user should receive only the minimum permissions necessary to perform their assigned tasks.

---

## 💻 Task 3B: Virtual Machine Provisioning Using Amazon EC2

**Objective:** Explore the process of creating and managing cloud-based virtual machines.

Amazon EC2 (Elastic Compute Cloud) provides virtual servers hosted on AWS infrastructure.

### EC2 Components Explored

- Amazon Machine Images (AMIs)
- Instance Types
- Key Pair Configuration
- Networking
- Security Groups
- Storage Configuration

### Steps

1. Open the EC2 Dashboard.
2. Select Launch Instance.
3. Enter an instance name.
4. Explore available AMIs and instance types.
5. Review key pair configuration.
6. Explore networking and security groups.
7. Review storage configuration.

**Note:** Launching an EC2 instance is optional and should only be performed with instructor approval and after checking the account's applicable pricing and eligibility.

---

## 🌐 Task 3C: Virtual Networking Using Amazon VPC

**Objective:** Understand virtual networking and its components in AWS.

Amazon VPC (Virtual Private Cloud) provides a logically isolated virtual network within AWS.

### VPC Components Explored

- VPC
- Public Subnets
- Private Subnets
- Route Tables
- Internet Gateways
- Security Groups

### Network Architecture

A typical AWS network architecture consists of a VPC containing public and private subnets, route tables, internet gateways and security groups.

A public subnet can provide internet connectivity when routing and security configurations permit it. A private subnet generally does not have a direct route to an internet gateway.

---

## 📊 Task 3D: Cloud Monitoring Using Amazon CloudWatch

**Objective:** Understand cloud resource monitoring and performance observation.

Amazon CloudWatch is a monitoring and observability service that collects and displays metrics, logs and monitoring information.

### Activities

1. Open the CloudWatch Dashboard.
2. Explore the Metrics section.
3. Identify metrics organised by AWS services.
4. Observe metric dimensions.
5. Explore the Alarms section.
6. Understand threshold-based alarm configuration.

**Example:** An alarm can notify an administrator when EC2 CPU utilisation exceeds a specified threshold for a defined period.

---

## ⌨️ Task 4: Basic AWS Operations Using AWS CLI

**Objective:** Perform AWS cloud operations through command-line instructions.

AWS CLI allows users to interact with AWS services directly from a terminal.

### 1. Verify AWS CLI Installation

```bash
aws --version
```

### 2. Verify AWS Account Identity

```bash
aws sts get-caller-identity
```

### 3. List Available S3 Buckets

```bash
aws s3 ls
```

### 4. Create a Local Sample File

```bash
mkdir cloud-lab6-cli
cd cloud-lab6-cli

echo "AWS CLI Cloud Storage Test" > sample.txt
```

### 5. Upload File to S3

```bash
aws s3 cp sample.txt s3://YOUR-BUCKET-NAME/sample.txt
```

### 6. List Objects in the Bucket

```bash
aws s3 ls s3://YOUR-BUCKET-NAME/
```

### 7. Download the File

```bash
aws s3 cp s3://YOUR-BUCKET-NAME/sample.txt downloaded.txt
```

### 8. Verify Downloaded File

```bash
cat downloaded.txt
```

### 9. Delete the Test Object

```bash
aws s3 rm s3://YOUR-BUCKET-NAME/sample.txt
```

Replace `YOUR-BUCKET-NAME` with the actual S3 bucket name.

---

## 🔒 Security & Cost Management

The following precautions should be followed during the experiment:

- Use only an authorised AWS account.
- Never share passwords, secret access keys or private keys.
- Avoid using the root account for routine operations.
- Enable Multi-Factor Authentication (MFA) wherever possible.
- Keep S3 Block Public Access enabled.
- Follow the principle of least privilege.
- Check applicable AWS pricing, credits and account eligibility before creating resources.
- Do not launch EC2 instances without instructor approval.
- Terminate unused instances and remove unnecessary resources.
- Delete temporary S3 objects and buckets after the practical.
- Review the AWS Billing Dashboard after completing the experiment.

**Important:** AWS Free Tier does not mean that every service or configuration is automatically free. Charges may depend on the account plan, Region, instance type, storage and applicable offers.

---

## 🎯 Learning Outcomes

After completing this experiment, students will be able to:

1. Set up and operate an Ubuntu virtual machine using VirtualBox.
2. Understand cloud storage using Amazon S3.
3. Perform basic file upload, download and deletion operations.
4. Understand identity and access management using AWS IAM.
5. Explore cloud-based virtual machines using Amazon EC2.
6. Understand virtual networking through Amazon VPC.
7. Explore cloud monitoring using Amazon CloudWatch.
8. Execute basic cloud storage operations using AWS CLI.

## 📸 Practical Screenshots

Screenshots demonstrating the practical implementation and command outputs are included in the repository's experiment documentation.

---

## 📖 Conclusion

This experiment provides practical exposure to cloud computing concepts and AWS services. It demonstrates how virtual machines, object storage, identity management, networking, monitoring and command-line tools can be used to understand and manage cloud infrastructure.

---

**Course:** Cloud Computing Laboratory  
**Experiment:** 06  
**Topic:** AWS Cloud Services and Open-Source Cloud Tools

## Author

**Debasmita Bose**

Cloud Computing Laboratory

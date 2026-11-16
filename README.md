
<h1 align="center">🌐 CLOUD COMPUTING LABORATORY</h1>

<h3 align="center">💻 Practical Implementations | Cloud Technologies | Virtualization | Distributed Computing</h3>

<p align="center">
  <img src="https://img.shields.io/badge/Domain-Cloud%20Computing-blue?style=for-the-badge&logo=icloud" />
  <img src="https://img.shields.io/badge/Platform-Ubuntu-orange?style=for-the-badge&logo=ubuntu" />
  <img src="https://img.shields.io/badge/Virtualization-VirtualBox-blue?style=for-the-badge&logo=virtualbox" />
  <img src="https://img.shields.io/badge/Language-Python-yellow?style=for-the-badge&logo=python" />
  <img src="https://img.shields.io/badge/Framework-Hadoop-green?style=for-the-badge&logo=apachehadoop" />
</p>

---

## 👩‍💻 ABOUT THIS REPOSITORY

Welcome to my **Cloud Computing Laboratory Repository!** 🚀

This repository contains practical experiments completed as part of the Cloud Computing Laboratory. It explores various cloud computing concepts, virtualization technologies, networking, distributed systems, cloud platforms, and application deployment.

The experiments provide hands-on experience with industry-relevant technologies and open-source tools.

### 🎯 Repository Highlights

- 🖥️ Virtual Machine Creation and Configuration
- 🌐 Network Connectivity and Virtual Network Topologies
- 🔗 Software-Defined Networking (SDN)
- ☁️ Amazon Web Services (AWS)
- 🤝 Software as a Service (SaaS)
- 🚀 Platform as a Service (PaaS)
- 🐍 Google App Engine and Flask
- 🐘 Hadoop HDFS and MapReduce

---

## 📑 TABLE OF CONTENTS

| No. | Experiment | Topic |
|:---:|---|---|
| 01 | [Experiment 1](#-experiment-1--virtual-machine-setup-and-configuration) | Virtual Machine Setup and Configuration |
| 02 | [Experiment 2](#-experiment-2--vm-cloning-and-network-connectivity) | VM Cloning and Network Connectivity |
| 03 | [Experiment 3](#-experiment-3--creation-of-a-simple-network-topology) | Network Topology Using Mininet |
| 04 | [Experiment 4](#-experiment-4--implementation-of-software-defined-networking) | Software-Defined Networking |
| 06 | [Experiment 6](#-experiment-6--familiarization-and-usage-of-cloud-services-using-aws) | AWS Cloud Services |
| 07 | [Experiment 7](#-experiment-7--familiarization-and-usage-of-collaborative-applications-saas) | Collaborative Applications (SaaS) |
| 08 | [Experiment 8](#-experiment-8--implementing-applications-using-google-app-engine-paas) | Google App Engine (PaaS) |
| 09 | [Experiment 9](#-experiment-9--hadoop-hdfs-and-mapreduce-word-count) | Hadoop HDFS and MapReduce |

---

# 🖥️ EXPERIMENT 1 — VIRTUAL MACHINE SETUP AND CONFIGURATION

<p>
<img src="https://img.shields.io/badge/Experiment-01-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Tool-VirtualBox-blue?style=flat-square&logo=virtualbox"/>
<img src="https://img.shields.io/badge/OS-Ubuntu-orange?style=flat-square&logo=ubuntu"/>
</p>

## 📌 Overview

This experiment focuses on creating, configuring, and verifying an Ubuntu Virtual Machine using Oracle VirtualBox.

### 🎯 Objective

To install and configure an open-source hypervisor, create an Ubuntu Virtual Machine, configure its virtual hardware resources, verify that the VM runs successfully, and install the required build tools and Linux kernel headers.

### 🛠️ Software and Environment

| Parameter | Configuration |
|---|---|
| Hypervisor | Oracle VirtualBox |
| Guest OS | Ubuntu |
| Architecture | 64-bit |
| Virtual Machine | Ubuntu 26.04 |
| Network Mode | NAT |
| Virtual CPU | 3 CPUs |
| Base Memory | 4096 MB |
| Virtual Hard Disk | 25 GB |

### ⚙️ Tasks Completed

**1. Install Oracle VirtualBox**

Installed and configured Oracle VirtualBox, an open-source virtualization platform used to create and manage virtual machines.

**2. Create a New Virtual Machine**

Created a new virtual machine with the following configuration:

- VM Name: Ubuntu 26.04
- Operating System: Linux
- Distribution: Ubuntu
- Version: Ubuntu (64-bit)

**3. Configure the Virtual Machine**

- CPU: 3 processors
- RAM: 4096 MB
- Storage: 25 GB
- Network: NAT

**4. Configure VM Hardware**

Verified CPU, memory, storage, and network settings through Oracle VirtualBox.

**5. Configure Ubuntu Installation**

Selected the Ubuntu ISO image and configured the required installation options.

**6. Start the Virtual Machine**

Started the Ubuntu virtual machine and proceeded with the boot process.

**7. Verify Ubuntu VM**

Verified that Ubuntu successfully booted and that the desktop environment was accessible.

**8. Install Required Build Tools**

```bash
sudo apt update
sudo apt install -y build-essential linux-headers-$(uname -r)
```

### ✅ Result

Successfully created, configured, and verified an Ubuntu virtual machine using Oracle VirtualBox.

---

# 🌐 EXPERIMENT 2 — VM CLONING AND NETWORK CONNECTIVITY

<p>
<img src="https://img.shields.io/badge/Experiment-02-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Network-NAT%20Network-green?style=flat-square"/>
<img src="https://img.shields.io/badge/OS-Ubuntu-orange?style=flat-square"/>
</p>

## 📌 Overview

This experiment demonstrates the cloning of an Ubuntu Virtual Machine using Oracle VirtualBox and establishing network connectivity between the original and cloned virtual machines.

Both VMs are connected to a customized NAT Network, allowing them to communicate through their assigned IP addresses.

### 🎯 Objective

- Clone an existing Ubuntu Virtual Machine.
- Create and configure a customized NAT Network.
- Connect both VMs to the same NAT Network.
- Verify network interfaces and IP configuration.
- Test communication using the `ping` command.
- Verify two-way connectivity through packet transmission.

### 🛠️ Tools and Technologies

- Oracle VirtualBox
- Ubuntu Linux
- NAT Network
- Linux Networking Commands

### ⚙️ Network Configuration

| Parameter | Configuration |
|---|---|
| Network Type | NAT Network |
| Network Name | MyNatNetwork |
| IPv4 Network | 10.0.2.0/24 |
| DHCP | Enabled |
| Network Interface | enp0s3 |

Both original and cloned Ubuntu VMs were connected to `MyNatNetwork`.

### 🖥️ Original VM Configuration

- Attached to: NAT Network
- Network Name: MyNatNetwork
- Virtual Cable: Connected

### 💻 Useful Networking Commands

**Check network interfaces and IP addresses:**

```bash
ip a
```

**Test connectivity between virtual machines:**

```bash
ping <destination-ip>
```

**Stop the ping process:**

```bash
Ctrl + C
```

### ✅ Result

Successfully cloned an Ubuntu virtual machine and configured network connectivity between the original and cloned VMs using a customized NAT Network.

---

# 🔀 EXPERIMENT 3 — CREATION OF A SIMPLE NETWORK TOPOLOGY

<p>
<img src="https://img.shields.io/badge/Experiment-03-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Tool-Mininet-green?style=flat-square"/>
<img src="https://img.shields.io/badge/Technology-Open%20vSwitch-orange?style=flat-square"/>
</p>

## 📌 Overview

This experiment demonstrates the creation, configuration, and testing of different network topologies using Mininet, an open-source network virtualization tool running on an Ubuntu Linux Virtual Machine.

The experiment focuses on creating Single-Switch, Tree, and Linear topologies and verifying communication between virtual network nodes.

### 🎯 Objective

To create and configure simple network topologies using Mininet and verify communication between virtual network nodes using basic Linux networking commands.

### 🛠️ Tools Used

- Ubuntu Linux
- Oracle VirtualBox
- Mininet
- Open vSwitch

### ⚙️ Mininet Installation and Setup

**1. Install Mininet**

```bash
sudo apt update
sudo apt install mininet -y
```

**2. Verify Installation**

```bash
mn --version
```

**3. Clean Previous Mininet Configurations**

```bash
sudo mn -c
```

### 📚 Topologies Explored

- Single-Switch Topology
- Tree Topology
- Linear Topology

### ✅ Result

Successfully explored Mininet and its network virtualization capabilities. Different network topologies were created and communication between virtual network nodes was tested.

---

# 🔗 EXPERIMENT 4 — IMPLEMENTATION OF SOFTWARE-DEFINED NETWORKING

<p>
<img src="https://img.shields.io/badge/Experiment-04-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/SDN-Ryu-purple?style=flat-square"/>
<img src="https://img.shields.io/badge/Network-Mininet-green?style=flat-square"/>
<img src="https://img.shields.io/badge/Protocol-OpenFlow%201.3-orange?style=flat-square"/>
</p>

## 📌 Overview

This experiment demonstrates the implementation of a Software-Defined Networking (SDN) environment using the Ryu SDN Controller, Mininet and Open vSwitch.

A single-switch topology containing three hosts is created in Mininet. The Ryu controller manages the virtual switch using OpenFlow 1.3.

Host connectivity is tested, switch flow-table entries are inspected, and a traffic-filtering rule is added and removed.

### 🎯 Objective

- Configure an SDN environment using open-source tools.
- Install and configure the Ryu SDN Controller.
- Create a virtual network topology using Mininet.
- Establish communication between Ryu and Open vSwitch.
- Verify connectivity between virtual hosts.
- Inspect OpenFlow flow-table entries.
- Demonstrate traffic filtering using a drop rule.

### 🛠️ Tools and Technologies

| Component | Technology |
|---|---|
| Operating System | Ubuntu Linux |
| Virtualization | Oracle VirtualBox |
| Network Emulator | Mininet |
| Virtual Switch | Open vSwitch |
| SDN Controller | Ryu 4.34 |
| Protocol | OpenFlow 1.3 |
| Python Version | Python 3.9.25 |

## ⚙️ Implementation Steps

### 1️⃣ Update Ubuntu and Install Required Packages

```bash
sudo apt update
sudo apt upgrade -y
sudo apt install -y git curl ca-certificates build-essential
sudo apt install -y mininet openvswitch-switch python3 python3-pip python3-venv
```

### 2️⃣ Start and Verify Open vSwitch

```bash
sudo systemctl enable --now openvswitch-switch
sudo systemctl status openvswitch-switch
sudo ovs-vsctl show
```

### 3️⃣ Install Python 3.9 Using uv

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source ~/.bashrc
uv python install 3.9
uv python find 3.9
```

### 4️⃣ Create a Python Virtual Environment

```bash
uv venv --python 3.9 ~/ryu-env39
source ~/ryu-env39/bin/activate
python --version
```

Install compatible packaging tools:

```bash
uv pip install --python ~/ryu-env39/bin/python setuptools==57.5.0 wheel
```

### 5️⃣ Install Ryu SDN Controller

```bash
git clone --branch v4.34 https://github.com/faucetsdn/ryu.git ~/ryu-source
cd ~/ryu-source
python setup.py install
```

Install runtime dependencies:

```bash
uv pip install --python ~/ryu-env39/bin/python eventlet msgpack netaddr oslo.config ovs routes six tinyrpc webob
```

Install a compatible Eventlet version:

```bash
uv pip install --python ~/ryu-env39/bin/python eventlet==0.30.2
```

### 6️⃣ Verify Ryu Installation

```bash
ryu-manager --version
```

Expected output:

```text
ryu-manager 4.34
```

Verify the OpenFlow application:

```bash
python -c "import ryu.app.simple_switch_13; print('OpenFlow 1.3 application OK')"
```

### 7️⃣ Start the Ryu Controller

```bash
source ~/ryu-env39/bin/activate
ryu-manager --ofp-tcp-listen-port 6653 ryu.app.simple_switch_13
```

Keep the controller running while using Mininet.

### 8️⃣ Create the Mininet Topology

```bash
sudo mn -c
sudo mn --topo single,3 --controller=remote,ip=127.0.0.1,port=6653 --switch ovsk,protocols=OpenFlow13
```

The topology contains:

- Three hosts: h1, h2 and h3
- One Open vSwitch: s1
- One remote controller: Ryu
- Communication protocol: OpenFlow 1.3

### 9️⃣ Verify Network Topology

```bash
nodes
net
```

Expected topology:

```text
h1 --- s1
h2 --- s1
h3 --- s1
```

### 🔟 Test Host Connectivity

```bash
pingall
h1 ping h2
```

Stop continuous ping:

```text
Ctrl + C
```

### 1️⃣1️⃣ Inspect OpenFlow Flow Tables

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

### 1️⃣2️⃣ Add a Traffic-Filtering Rule

```bash
sudo ovs-ofctl -O OpenFlow13 add-flow s1 "priority=100,in_port=1,actions=drop"
```

Verify the updated flow table:

```bash
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

### 1️⃣3️⃣ Remove the Traffic-Filtering Rule

```bash
sudo ovs-ofctl -O OpenFlow13 del-flows s1
sudo ovs-ofctl -O OpenFlow13 dump-flows s1
```

### 1️⃣4️⃣ Exit and Clean Up

```bash
exit
sudo mn -c
```

Stop the Ryu controller using `Ctrl + C`.

### ⚠️ Important Execution Notes

- Keep the Ryu controller running before starting Mininet.
- Use separate terminals for Ryu, Mininet and Open vSwitch commands.
- `nodes`, `net` and `pingall` must run inside Mininet CLI.
- `ovs-ofctl` commands must run in the Ubuntu terminal.
- Verify port 6653 if the controller connection fails.
- Port 1 (`s1-eth1`) is connected to h1 in this topology.

### 📊 Results and Observations

- Ryu SDN Controller configured successfully.
- Three-host, single-switch topology created.
- OpenFlow 1.3 communication established.
- Host connectivity tested using ping commands.
- Flow-table entries inspected.
- Traffic-filtering rule added and removed.

### ✅ Result

Successfully implemented a basic Software-Defined Networking environment using Ryu, Mininet and Open vSwitch.

---

# ☁️ EXPERIMENT 6 — FAMILIARIZATION AND USAGE OF CLOUD SERVICES USING AWS

<p>
<img src="https://img.shields.io/badge/Experiment-06-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Cloud-AWS-orange?style=flat-square&logo=amazonaws"/>
<img src="https://img.shields.io/badge/OS-Ubuntu-E95420?style=flat-square&logo=ubuntu"/>
</p>

## 📌 Aim

To become familiar with different cloud services and perform basic cloud operations using Amazon Web Services (AWS), Ubuntu Linux, Oracle VirtualBox, and AWS Command Line Interface (CLI).

### 🛠️ Technologies and Tools Used

- Amazon Web Services (AWS)
- Ubuntu Linux
- Oracle VirtualBox
- Amazon S3
- AWS IAM
- Amazon EC2
- Amazon VPC
- Amazon CloudWatch
- AWS CLI / AWS CloudShell

## 📚 Experiment Overview

| Task | Practical Area | Description |
|---|---|---|
| 1 | Virtual Machine Setup | Ubuntu using VirtualBox |
| 2 | Cloud Storage | Amazon S3 operations |
| 3 | Cloud Service Exploration | IAM, EC2 and VPC |
| 4 | Monitoring and CLI | CloudWatch and AWS CLI |

## 🖥️ TASK 1 — Virtual Machine Setup

**Objective:** Set up an Ubuntu virtual machine using Oracle VirtualBox.

### Steps Performed

1. Created a virtual machine in Oracle VirtualBox.
2. Installed Ubuntu Linux.
3. Updated package lists and installed packages.
4. Installed basic utilities.
5. Executed Linux terminal commands.

### Commands

```bash
sudo apt update
sudo apt upgrade -y
```

## 🪣 TASK 2 — Cloud Storage Using Amazon S3

**Objective:** Understand object storage and perform basic storage operations using Amazon S3.

Amazon S3 (Simple Storage Service) is an object storage service used to store and retrieve data over the internet.

### Steps Performed

1. Accessed AWS Management Console.
2. Opened Amazon S3.
3. Created a globally unique S3 bucket.
4. Selected an AWS Region.
5. Kept Block Public Access enabled.
6. Retained default encryption settings.
7. Created a sample text file in Ubuntu.
8. Uploaded the file to S3.
9. Downloaded the uploaded object.
10. Verified its contents and deleted the test object and empty bucket.

### Create a Sample File

```bash
mkdir cloud-lab6
cd cloud-lab6

echo "Cloud Computing Lab Experiment 6" > lab-note.txt

cat lab-note.txt
```

### Expected Result

A private S3 bucket is created successfully, and a sample file is uploaded, downloaded, verified and deleted.

## 🔐 TASK 3A — Identity and Access Management (IAM)

AWS IAM controls who can access AWS services and what actions they can perform.

### Concepts Explored

- **Users:** Identities representing users.
- **Groups:** Collections of IAM users.
- **Roles:** Identities providing temporary permissions.
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

**Principle of Least Privilege:** Every user should receive only the minimum permissions necessary.

## 💻 TASK 3B — Virtual Machine Provisioning Using Amazon EC2

Amazon EC2 (Elastic Compute Cloud) provides virtual servers hosted on AWS infrastructure.

### EC2 Components Explored

- Amazon Machine Images (AMIs)
- Instance Types
- Key Pair Configuration
- Networking
- Security Groups
- Storage Configuration

### Steps

1. Opened EC2 Dashboard.
2. Selected Launch Instance.
3. Entered an instance name.
4. Explored available AMIs and instance types.
5. Reviewed key pair configuration.
6. Explored networking and security groups.
7. Reviewed storage configuration.

**Note:** Launching an EC2 instance is optional and should be performed only with instructor approval and after checking applicable pricing.

## 🌐 TASK 3C — Virtual Networking Using Amazon VPC

Amazon VPC provides a logically isolated virtual network within AWS.

### VPC Components Explored

- VPC
- Public Subnets
- Private Subnets
- Route Tables
- Internet Gateways
- Security Groups

A typical AWS network architecture consists of a VPC containing public and private subnets, route tables, internet gateways and security groups.

## 📊 TASK 3D — Cloud Monitoring Using Amazon CloudWatch

Amazon CloudWatch is a monitoring and observability service that collects and displays metrics, logs and monitoring information.

### Activities

1. Opened CloudWatch Dashboard.
2. Explored the Metrics section.
3. Identified metrics organised by AWS services.
4. Observed metric dimensions.
5. Explored the Alarms section.
6. Understood threshold-based alarm configuration.

**Example:** An alarm can notify an administrator when EC2 CPU utilisation exceeds a specified threshold.

## ⌨️ TASK 4 — Basic AWS Operations Using AWS CLI

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

### 4. Create a Sample File

```bash
mkdir cloud-lab6-cli
cd cloud-lab6-cli

echo "AWS CLI Cloud Storage Test" > sample.txt
```

### 5. Upload File to S3

```bash
aws s3 cp sample.txt s3://YOUR-BUCKET-NAME/sample.txt
```

### 6. List Objects

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

## 🔒 Security and Cost Management

- Use only an authorised AWS account.
- Never share passwords, secret keys or private keys.
- Avoid using the root account for routine operations.
- Enable Multi-Factor Authentication.
- Keep S3 Block Public Access enabled.
- Follow least-privilege access.
- Check AWS pricing before creating resources.
- Terminate unused instances.
- Delete temporary resources.
- Review the AWS Billing Dashboard.

**Important:** AWS Free Tier does not mean every service or configuration is automatically free.

## 🎯 Learning Outcomes

1. Understand cloud storage using Amazon S3.
2. Perform file upload, download and deletion.
3. Understand IAM.
4. Explore EC2 virtual machines.
5. Understand VPC networking.
6. Explore CloudWatch monitoring.
7. Execute AWS CLI commands.

### ✅ Result

Successfully explored AWS services, including S3, IAM, EC2, VPC and CloudWatch, and learned basic cloud operations using AWS CLI.

### 📝 Conclusion

This experiment provided practical exposure to cloud services and demonstrated how virtual machines, object storage, identity management, networking and monitoring can be used to manage cloud infrastructure.

---

# 🤝 EXPERIMENT 7 — FAMILIARIZATION AND USAGE OF COLLABORATIVE APPLICATIONS (SaaS)

<p>
<img src="https://img.shields.io/badge/Experiment-07-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Cloud%20Model-SaaS-green?style=flat-square"/>
<img src="https://img.shields.io/badge/Platform-Google%20Workspace-4285F4?style=flat-square&logo=google"/>
</p>

## 📌 Aim

To understand the Software as a Service (SaaS) cloud delivery model and demonstrate web-based applications for document creation, spreadsheet management, presentation creation, online meetings and real-time collaboration.

### 🛠️ Applications Used

- Google Docs
- Google Sheets
- Google Slides
- Google Meet
- Google Drive
- Web Browser
- Internet Connection

## 📚 Introduction

**Software as a Service (SaaS)** is a cloud-based software delivery model in which applications are hosted by a service provider and accessed through the internet.

Users can access software through a web browser without installing or managing the underlying infrastructure locally.

## 🧪 Practical Implementation

### 📝 1. Google Docs — Collaborative Document Editing

**Objective:** Create, edit and share a document using Google Docs.

**Activities Performed:**

1. Opened Google Docs.
2. Created a document titled `Cloud Computing Lab 7 – Collaborative Document`.
3. Added an introduction to SaaS and its features.
4. Created and formatted a table.
5. Shared the document with another Google account.
6. Assigned Editor permissions.
7. Performed collaborative editing.
8. Added comments and explored Version History.

**Concepts Observed:**

- Online document editing
- Real-time collaboration
- Sharing permissions
- Comments and version history
- Automatic cloud saving

### 📊 2. Google Sheets — Cloud-Based Spreadsheet Management

**Objective:** Create and manage a spreadsheet using Google Sheets.

**Activities Performed:**

1. Created a spreadsheet titled `Cloud Computing Lab 7 – Collaborative Spreadsheet`.
2. Entered student details and marks.
3. Organised data using rows and columns.
4. Applied spreadsheet formulas.
5. Shared the spreadsheet with a collaborator.
6. Observed collaborative editing and comments.

**Sample Dataset:**

| Student ID | Name | Subject | Marks |
|---|---|---|---:|
| S101 | Student A | Cloud Computing | 82 |
| S102 | Student B | Cloud Computing | 75 |
| S103 | Student C | Cloud Computing | 91 |
| S104 | Student D | Cloud Computing | 68 |
| S105 | Student E | Cloud Computing | 87 |

**Formulas Used:**

```excel
=SUM(D3:D7)
=AVERAGE(D3:D7)
=MAX(D3:D7)
=MIN(D3:D7)
```

**Calculated Results:**

| Operation | Result |
|---|---:|
| Total Marks | 403 |
| Average Marks | 80.6 |
| Highest Marks | 91 |
| Lowest Marks | 68 |

### 🎨 3. Google Slides — Cloud-Based Presentation

**Objective:** Create, edit and share a presentation using Google Slides.

**Activities Performed:**

1. Created a presentation titled `Software as a Service (SaaS)`.
2. Created four slides.
3. Added an introduction to SaaS.
4. Included examples of SaaS applications.
5. Described the advantages of SaaS.
6. Formatted slide content.
7. Shared the presentation with another Google account.
8. Assigned Editor permissions.
9. Explored collaborative slide editing and comments.

**Topics Covered:**

- Introduction to SaaS
- What is SaaS?
- Google Docs and Google Sheets
- Microsoft 365 and Microsoft Teams
- Salesforce
- Advantages of SaaS

### 🎥 4. Google Meet — Online Meeting and Communication

**Objective:** Explore online meeting creation and communication using Google Meet.

**Activities Performed:**

1. Opened Google Meet through a web browser.
2. Selected the New Meeting option.
3. Generated a meeting link.
4. Viewed meeting joining information.
5. Copied and explored the meeting link.
6. Explored the meeting interface and controls.
7. Observed the meeting dashboard.

**Concepts Observed:**

- Online video conferencing
- Meeting link generation
- Remote communication
- Internet-based collaboration

## ⭐ Key Features of SaaS Observed

| Feature | Description |
|---|---|
| Internet Accessibility | Applications accessible through the internet |
| Real-Time Collaboration | Multiple users can work together |
| Automatic Updates | Updates managed by service providers |
| Cloud Storage | Data stored using cloud infrastructure |
| Reduced Maintenance | No need to manage underlying servers |
| Scalability | Usage can expand according to requirements |

## 🎯 Learning Outcomes

1. Understand the SaaS model.
2. Create and edit cloud-based documents.
3. Perform calculations using Google Sheets.
4. Design presentations using Google Slides.
5. Generate online meeting links using Google Meet.
6. Understand real-time collaboration.
7. Explore sharing permissions and version history.

### 📸 Practical Screenshots

Screenshots documenting the practical implementation of Google Docs, Google Sheets, Google Slides and Google Meet are included in the experiment report.

### ✅ Result

Successfully explored Google Docs, Google Sheets, Google Slides and Google Meet, including document editing, spreadsheet calculations, presentation creation, online meeting generation and collaborative sharing.

### 📝 Conclusion

This experiment demonstrated how SaaS applications provide ready-to-use software over the internet. Google Workspace simplifies document management, data processing, presentation creation and online communication while enabling real-time collaboration.

---

# 🚀 EXPERIMENT 8 — IMPLEMENTING APPLICATIONS USING GOOGLE APP ENGINE (PaaS)

<p>
<img src="https://img.shields.io/badge/Experiment-08-blue?style=flat-square"/>
<img src="https://img.shields.io/badge/Cloud%20Model-PaaS-green?style=flat-square"/>
<img src="https://img.shields.io/badge/Language-Python-3776AB?style=flat-square&logo=python"/>
<img src="https://img.shields.io/badge/Framework-Flask-black?style=flat-square&logo=flask"/>
<img src="https://img.shields.io/badge/Platform-Google%20Cloud-4285F4?style=flat-square&logo=googlecloud"/>
</p>

## 📌 Aim

To become familiar with Platform as a Service (PaaS) and implement, deploy and manage a simple web application using Google App Engine.

### 🛠️ Technologies and Tools Used

- Google Cloud Platform (GCP)
- Google App Engine
- Python
- Flask Framework
- Google Cloud CLI (`gcloud`)
- Ubuntu Linux
- Terminal
- Web Browser

## 📚 Introduction

**Platform as a Service (PaaS)** is a cloud computing service model that provides a platform for developing, running and managing applications without requiring users to manage the underlying infrastructure.

Google App Engine is a fully managed PaaS platform provided by Google Cloud.

## 🧪 Experiment Overview

| Task | Practical Area | Description |
|---|---|---|
| 1 | PaaS and App Engine Setup | Create a Google Cloud project |
| 2 | Web Application Development | Develop a Flask application |
| 3 | Google Cloud CLI Setup | Install and configure CLI |
| 4 | Deployment and Management | Explore application deployment and management |

## ☁️ TASK 1 — PaaS and Google App Engine Setup

**Objective:** Understand PaaS and configure a Google Cloud project for App Engine.

### Steps Performed

1. Opened Google Cloud Console.
2. Signed in using a Google account.
3. Created a project named `Cloud-Lab8`.
4. Opened the App Engine Dashboard.
5. Explored the App Engine interface.
6. Enabled the App Engine Admin API.

### Project Details

| Property | Value |
|---|---|
| Project Name | Cloud-Lab8 |
| Project ID | `cloud-lab8-514907` |
| Cloud Platform | Google Cloud Platform |
| PaaS Service | Google App Engine |

### Enable App Engine Admin API

```bash
gcloud services enable appengine.googleapis.com
```

Verify enabled services:

```bash
gcloud services list --enabled
```

## 🐍 TASK 2 — Develop a Web Application Using Flask

**Objective:** Develop and run a simple Python web application locally.

### Step 1: Create Project Directory

```bash
mkdir cloud-lab8
cd cloud-lab8
```

### Step 2: Create `main.py`

```python
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return """
    <h1>Cloud Computing Lab 8</h1>
    <p>Application successfully implemented using Google App Engine.</p>
    <p>This application demonstrates Platform as a Service (PaaS).</p>
    """

if __name__ == "__main__":
    app.run(host="127.0.0.1", port=8080)
```

### Step 3: Create `requirements.txt`

```text
Flask
```

### Step 4: Create and Activate Virtual Environment

```bash
python3 -m venv venv
source venv/bin/activate
```

### Step 5: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 6: Run Flask Application

```bash
python main.py
```

### Step 7: Access Application

Open the browser:

```text
http://127.0.0.1:8080
```

**Expected Output:**

- Cloud Computing Lab 8
- Application successfully implemented using Google App Engine.
- This application demonstrates Platform as a Service (PaaS).

## ⚙️ TASK 3 — Google Cloud CLI Installation and Configuration

**Objective:** Install and configure Google Cloud CLI to interact with Google Cloud services through the terminal.

### Step 1: Install Google Cloud CLI

```bash
sudo apt-get update
```

Install required utilities:

```bash
sudo apt-get install ca-certificates gnupg curl -y
```

Add Google Cloud package signing key:

```bash
curl https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo gpg --dearmor -o /usr/share/keyrings/cloud.google.gpg
```

Add the Google Cloud CLI repository:

```bash
echo "deb [signed-by=/usr/share/keyrings/cloud.google.gpg] https://packages.cloud.google.com/apt cloud-sdk main" | sudo tee -a /etc/apt/sources.list.d/google-cloud-sdk.list
```

Install Google Cloud CLI:

```bash
sudo apt-get update
sudo apt-get install google-cloud-cli -y
```

### Step 2: Verify Installation

```bash
gcloud --version
```

### Step 3: Authenticate Google Cloud CLI

```bash
gcloud auth login
```

Complete authentication through the browser.

### Step 4: List Google Cloud Projects

```bash
gcloud projects list
```

### Step 5: Select the Project

```bash
gcloud config set project cloud-lab8-514907
```

Verify:

```bash
gcloud config get-value project
```

### Step 6: Create `app.yaml`

```bash
nano app.yaml
```

Add the following configuration:

```yaml
runtime: python312
```

Save and verify:

```bash
cat app.yaml
```

## 🚀 TASK 4 — Application Deployment and Management

**Objective:** Deploy the Flask application using Google App Engine and explore application management features.

### Step 1: Create App Engine Application

Open Google Cloud Console and navigate to the App Engine Dashboard.

Select the appropriate region according to lab requirements.

**Note:** The region selected during App Engine application creation is generally permanent and cannot be changed later.

### Step 2: Deploy Application

After satisfying the application creation and billing prerequisites:

```bash
gcloud app deploy
```

Confirm deployment when prompted.

### Step 3: Open Deployed Application

```bash
gcloud app browse
```

### Step 4: List Application Versions

```bash
gcloud app versions list
```

### Step 5: View Application Logs

```bash
gcloud app logs tail
```

### Step 6: Update Application

Modify the message in `main.py`, for example:

```python
<p>Welcome to Cloud Computing Lab 8 - Version 2!</p>
```

Deploy again:

```bash
gcloud app deploy
```

### Step 7: Explore App Engine Management Features

- Services
- Versions
- Instances
- Logs
- Monitoring
- Traffic Management

## 📊 Important Concepts

| Concept | Description |
|---|---|
| PaaS | Managed application development and deployment platform |
| Google App Engine | Managed application hosting service |
| Flask | Lightweight Python web framework |
| `gcloud` CLI | Google Cloud command-line tool |
| `app.yaml` | App Engine runtime configuration |
| Application Versions | Different deployed application versions |
| Application Logs | Records of application activity |

## 🔒 Billing and Cost Considerations

- Google Cloud billing may be required for deployment.
- Check applicable pricing and free usage limits.
- Do not add a payment method without authorisation.
- Monitor cloud resource usage.
- Use an authorised Google Cloud account.

**Practical Note:** Local Flask development does not require Google Cloud deployment. Actual App Engine deployment requires the necessary project configuration and billing eligibility.

## 🎯 Learning Outcomes

1. Understand the PaaS model.
2. Become familiar with Google App Engine.
3. Develop a web application using Python and Flask.
4. Configure a Python virtual environment.
5. Install and authenticate Google Cloud CLI.
6. Configure a Google Cloud project.
7. Understand application deployment.
8. Explore application versions, logs and monitoring.

## 📸 Practical Screenshots

Screenshots documenting the experiment include:

- Google Cloud project creation
- App Engine Dashboard
- Google Cloud CLI installation
- Project authentication and configuration
- Flask application development
- Localhost application execution
- `app.yaml` configuration
- App Engine API activation
- Deployment and management activities, where completed

### ✅ Result

A simple Flask web application was developed and successfully executed in the local Ubuntu environment. Google Cloud project configuration, CLI authentication, API activation and application configuration were also performed.

Actual App Engine deployment remains subject to billing activation and successful application creation.

### 📝 Conclusion

This experiment provided practical exposure to the Platform as a Service (PaaS) model using Google App Engine. A basic web application was developed using Flask and tested locally. Google Cloud CLI was installed and configured to interact with Google Cloud resources.

---

# 🐘 EXPERIMENT 9 — HADOOP HDFS AND MAPREDUCE WORD COUNT

<p>
<img src="https://img.shields.io/badge/Experiment-09-blue?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Framework-Hadoop%203.5.0-green?style=for-the-badge&logo=apachehadoop"/>
<img src="https://img.shields.io/badge/Language-Java-orange?style=for-the-badge&logo=openjdk"/>
<img src="https://img.shields.io/badge/Storage-HDFS-blue?style=for-the-badge"/>
<img src="https://img.shields.io/badge/Processing-MapReduce-purple?style=for-the-badge"/>
</p>

<h2 align="center">✨ HADOOP HDFS AND MAPREDUCE ✨</h2>

<h3 align="center">WORD COUNT IMPLEMENTATION</h3>

<p align="center">
  <b>EXPERIMENT NO. 09</b>
</p>

## 🎯 AIM

To set up a Hadoop cluster in a Linux environment and develop, execute and verify a MapReduce application using the Hadoop Distributed File System (HDFS) and Hadoop MapReduce framework.

## 📌 Overview

This experiment demonstrates Hadoop cluster configuration, HDFS operations, and the development and execution of a Java-based MapReduce Word Count application.

The experiment covers:

- Hadoop environment configuration
- SSH setup
- HDFS directory management
- Java program compilation
- MapReduce execution
- Hadoop cluster verification

## 🛠️ Technologies Used

| Category | Technology |
|---|---|
| Operating System | Ubuntu Linux |
| Framework | Apache Hadoop 3.5.0 |
| Programming Language | Java |
| Distributed Storage | HDFS |
| Processing Framework | MapReduce |
| Resource Management | YARN |
| Terminal Editor | Nano |
| Remote Access | OpenSSH |

## ⚙️ Hadoop Configuration Files

| Configuration File | Purpose |
|---|---|
| `hadoop-env.sh` | Configures JAVA_HOME |
| `core-site.xml` | Defines the default filesystem URI |
| `hdfs-site.xml` | Configures NameNode and DataNode directories |
| `mapred-site.xml` | Configures MapReduce execution using YARN |

## 🧩 MapReduce Application

The WordCount application consists of two main components.

### 1️⃣ TokenizerMapper

The Mapper performs the following operations:

- Reads input text line by line.
- Splits each line into individual words.
- Emits each word with an intermediate value of 1.

### 2️⃣ IntSumReducer

The Reducer performs the following operations:

- Receives words and their associated values.
- Adds the values for each word.
- Produces the final word-frequency count.

## 📂 Input Dataset

The `input.txt` file contains sample text related to:

- Cloud computing
- Distributed systems
- Hadoop processing
- Distributed storage
- MapReduce
- Parallel processing

## 🚀 IMPLEMENTATION STEPS

### 1️⃣ Hadoop Environment Configuration

Configure the Java environment and Hadoop XML configuration files.

### 2️⃣ SSH Configuration

Install OpenSSH and generate an ED25519 SSH key pair for passwordless local authentication.

### 3️⃣ Start Hadoop Services

Start HDFS and YARN services.

Check running Java processes:

```bash
jps
```

Expected Hadoop processes:

- NameNode
- DataNode
- SecondaryNameNode
- ResourceManager
- NodeManager

### 4️⃣ HDFS Directory Creation

Create the required HDFS directories:

```bash
hdfs dfs -mkdir -p /user/student/cloud-lab9/input
```

Upload the input file:

```bash
hdfs dfs -put input.txt /user/student/cloud-lab9/input/
```

### 5️⃣ Compile the Java Program

Set the Hadoop classpath:

```bash
export HADOOP_CLASSPATH=$(hadoop classpath)
```

Compile the Java source file:

```bash
javac -classpath "$HADOOP_CLASSPATH" -d . WordCount.java
```

### 6️⃣ Create JAR Package

Package the compiled classes:

```bash
jar -cvf wordcount.jar -C . .
```

### 7️⃣ Execute MapReduce Application

Run the WordCount application:

```bash
hadoop jar wordcount.jar WordCount \
/user/student/cloud-lab9/input \
/user/student/cloud-lab9/output
```

The Hadoop framework processes the input and generates the word-count output.

### 8️⃣ Verify HDFS Operations

**List HDFS directories:**

```bash
hdfs dfs -ls /user/student/cloud-lab9/input
```

**Check disk usage:**

```bash
hdfs dfs -du -h /user/student/cloud-lab9
```

**Check filesystem capacity:**

```bash
hdfs dfs -df -h /
```

**Display input file contents:**

```bash
hdfs dfs -cat /user/student/cloud-lab9/input/input.txt
```

**Verify HDFS health:**

```bash
hdfs fsck /user/student/cloud-lab9/input -files -blocks -locations
```

### 9️⃣ Stop Hadoop Services

Stop YARN and HDFS services using their respective stop scripts.

Check remaining Java processes:

```bash
jps
```

## 📸 SCREENSHOTS AND OBSERVATIONS

### 🖼️ COLLAGE 1 — HADOOP CONFIGURATION AND INITIAL SETUP

This collage demonstrates the initial Hadoop setup, configuration files, Java MapReduce source code, SSH configuration, and service startup.

**Screenshot-wise descriptions:**

| No. | Screenshot | Description |
|:---:|---|---|
| 01 | `mapred-site.xml` | Configuration of the MapReduce framework and Hadoop environment properties. |
| 02 | Compile and Package | Compilation of Java classes and creation of the WordCount JAR package. |
| 03 | `IntSumReducer.java` | Java Reducer implementation for calculating the total count of each word. |
| 04 | `WordCount.java` | Mapper implementation using StringTokenizer to extract individual words. |
| 05 | Start DFS, YARN & Check JPS | Starting Hadoop services and verifying active Hadoop daemons. |
| 06 | HDFS Directory Creation | Creation and inspection of HDFS directories for input and output. |
| 07 | `input.txt` | Preparation of the sample text dataset for MapReduce processing. |
| 08 | SSH Key Generation | Creation of an ED25519 SSH key pair for passwordless authentication. |
| 09 | OpenSSH Installation | Installation and configuration of OpenSSH server and client. |
| 10 | `hadoop-env.sh` | Configuration of the Java environment using JAVA_HOME. |
| 11 | `hdfs-site.xml` | Configuration of NameNode and DataNode storage directories. |
| 12 | `core-site.xml` | Configuration of the default HDFS filesystem URI. |
| 13 | `mapred-site.xml` Final | Final MapReduce configuration. |

### 🖼️ COLLAGE 2 — HADOOP EXECUTION AND VERIFICATION

This collage demonstrates Hadoop execution, filesystem verification, storage information, cluster monitoring, and MapReduce job completion.

**Screenshot-wise descriptions:**

| No. | Screenshot | Description |
|:---:|---|---|
| 01 | HDFS Final Verification | Execution of filesystem commands to inspect directories, file contents, disk usage and HDFS status. |
| 02 | HDFS Filesystem Health | Verification of block replication, storage capacity and filesystem health. |
| 03 | HDFS Block Information | Inspection of filesystem blocks, replication details and storage information. |
| 04 | YARN ResourceManager Dashboard | Viewing cluster metrics, active nodes, resource allocation and application status. |
| 05 | NameNode Overview | Verification of the active NameNode, Hadoop version, cluster information and HDFS storage summary. |
| 06 | MapReduce Execution Logs | Monitoring application submission, map and reduce task execution, and job completion. |
| 07 | Hadoop Service Shutdown | Stopping Hadoop services and checking the remaining Java processes. |

## 📊 OBSERVATIONS

- Hadoop configuration files were successfully prepared.
- SSH authentication was configured for local Hadoop service management.
- HDFS directories were created and the input dataset was uploaded.
- The Java WordCount application was compiled and packaged into a JAR file.
- The MapReduce job was submitted and executed through Hadoop.
- The execution logs showed successful completion of map and reduce tasks.
- HDFS filesystem verification reported **HEALTHY** status.
- NameNode and ResourceManager dashboards were used to inspect cluster status.

## 🧠 LEARNING OUTCOMES

After completing this experiment, the following concepts were understood:

1. Hadoop cluster configuration.
2. HDFS directory and file management.
3. SSH authentication and Hadoop service management.
4. Java-based MapReduce programming.
5. Mapper and Reducer functionality.
6. Java compilation and JAR packaging.
7. MapReduce job execution using YARN.
8. HDFS filesystem verification.
9. NameNode and ResourceManager monitoring.

## ✅ RESULT

The Hadoop environment was configured successfully. The Java-based MapReduce WordCount application was developed, compiled, packaged, and executed using HDFS and YARN. The Hadoop cluster and HDFS operations were verified successfully.

## 📝 CONCLUSION

This experiment provided practical knowledge of Hadoop Distributed File System and MapReduce programming.

The Hadoop environment was configured in Ubuntu Linux, and a Java-based WordCount application was developed and executed. HDFS operations, Hadoop service management, YARN execution and cluster verification were explored.

The experiment demonstrated how Hadoop processes large datasets using distributed storage and parallel processing techniques.

---

# 🌟 OVERALL LEARNING OUTCOMES

Through these Cloud Computing Laboratory experiments, I gained practical exposure to several important technologies and concepts.

| Area | Skills Acquired |
|---|---|
| Virtualization | Virtual Machine creation and management |
| Networking | NAT Networks and connectivity testing |
| Network Virtualization | Mininet and Open vSwitch |
| SDN | Ryu Controller and OpenFlow |
| Cloud Storage | Amazon S3 |
| Cloud Security | AWS IAM |
| Cloud Infrastructure | Amazon EC2 and VPC |
| Monitoring | Amazon CloudWatch |
| SaaS | Google Workspace |
| PaaS | Google App Engine |
| Web Development | Python and Flask |
| Distributed Computing | Hadoop HDFS |
| Big Data Processing | Java MapReduce |
| Resource Management | YARN |

---

# 💻 TECHNOLOGIES & TOOLS

<p align="center">
  <img src="https://skillicons.dev/icons?i=ubuntu,java,python,bash,git,github,aws,gcp&perline=4" />
</p>

### Additional Tools

- Oracle VirtualBox
- Apache Hadoop
- Mininet
- Open vSwitch
- Ryu SDN Controller
- Google Docs
- Google Sheets
- Google Slides
- Google Meet
- AWS CLI
- Google Cloud CLI

---

# 📂 REPOSITORY STRUCTURE

```text
☁️ Cloud-Computing-Lab/
│
├── 📁 Experiment-1/
│   └── 🖥️ Virtual Machine Setup and Configuration
│
├── 📁 Experiment-2/
│   └── 🌐 VM Cloning and Network Connectivity
│
├── 📁 Experiment-3/
│   └── 🔀 Mininet Network Topology Creation
│
├── 📁 Experiment-4/
│   └── 🔗 SDN Implementation Using Ryu and Mininet
│
├── 📁 Experiment-6/
│   └── ☁️ AWS Cloud Services
│
├── 📁 Experiment-7/
│   └── 🤝 Collaborative Applications (SaaS)
│
├── 📁 Experiment-8/
│   └── 🚀 Google App Engine (PaaS)
│
├── 📁 Experiment-9/
│   └── 🐘 Hadoop HDFS and MapReduce
│
└── 📄 README.md
```

---

# 👩‍💻 AUTHOR

<h2 align="center">✨ Debasmita Bose ✨</h2>

<p align="center">
  🎓 B.Tech — Computer Science and Engineering
  <br/>
  ☁️ Cloud Computing Enthusiast
  <br/>
  💻 Exploring Software Development, AI and Cloud Technologies
</p>

<p align="center">
  <a href="https://github.com/DebasmitaBose0">
    <img src="https://img.shields.io/badge/GitHub-DebasmitaBose0-181717?style=for-the-badge&logo=github"/>
  </a>
  <a href="https://www.linkedin.com/in/debasmita-bose-0002b329a/">
    <img src="https://img.shields.io/badge/LinkedIn-Connect-blue?style=for-the-badge&logo=linkedin"/>
  </a>
</p>

---

<h3 align="center">💙 THANK YOU FOR VISITING! 💙</h3>

<p align="center">
  <b>Keep Learning • Keep Exploring • Keep Building 🚀</b>
</p>

<p align="center">
  ⭐ If you find this repository useful, consider giving it a star! ⭐
</p>

<p align="center">
  <i>Made with ❤️ and dedication by Debasmita Bose</i>
</p>
